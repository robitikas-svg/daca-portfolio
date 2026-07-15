1.Müüki linnade kaupa.

SELECT 
    c.city AS linn, 
    COUNT(s.sale_id) AS tellimuste_arv, 
    SUM(s.total_price) AS kogukaive, 
    AVG(s.total_price) AS keskmine_tellimus
FROM sales s
INNER JOIN customers c ON s.customer_id = c.customer_id
GROUP BY c.city
ORDER BY kogukaive DESC;# Nädal 4: SQL Basics

2. päring, mis leiab tooted, kus kategoorias on müüdud üle ühiku.


SELECT 
    p.category AS kategooria, 
    SUM(s.quantity) AS myydud_kogus_kokku, 
    ROUND(AVG(p.retail_price), 2) AS keskmine_jaemyygihind, 
    COUNT(DISTINCT p.product_id) AS erinevate_toodete_arv
FROM products p
INNER JOIN sales s ON p.product_id = s.product_id
GROUP BY p.category
HAVING SUM(s.quantity) > 500
ORDER BY myydud_kogus_kokku DESC;


Meeskonnatöö 3.
Kliendigruppide analüüs CTE ja aknafunktsiooniga
WITH kliendi_kokkuvote AS (
    SELECT
        c.customer_id,
        c.first_name || ' ' || c.last_name AS nimi,
        c.city,
        COUNT(o.sale_id) AS tellimuste_arv,
        SUM(o.total_price) AS kogukäive
    FROM customers c
    JOIN sales o ON c.customer_id = o.customer_id
    GROUP BY c.customer_id, c.first_name, c.last_name, c.city
)
SELECT
    nimi,
    city,
    tellimuste_arv,
    kogukäive,
    CASE
        WHEN kogukäive > 500 THEN 'VIP'       -- Piir: üle 500€ (strateegiline ostja)
        WHEN kogukäive > 150 THEN 'Regular'   -- Piir: 150€ - 500€ (püsiklient)
        ELSE 'Uus'                            -- Piir: alla 150€ (potentsiaalne kasv)
    END AS segment,
    -- Window function koha leidmiseks linnas
    RANK() OVER (
        PARTITION BY city
        ORDER BY kogukäive DESC
    ) AS koht_linnas
FROM kliendi_kokkuvote
ORDER BY kogukäive DESC;

TOP 10 klienti 

SELECT
    c.first_name || ' ' || c.last_name AS nimi,
    SUM(s.total_price) AS kogukäive,
    COUNT(s.sale_id) AS ostude_arv
FROM sales s
JOIN customers c ON s.customer_id = c.customer_id
GROUP BY c.customer_id, c.first_name, c.last_name
HAVING COUNT(s.sale_id) >= 2 -- Ainult kliendid, kes on naasnud
ORDER BY kogukäive DESC
LIMIT 10;

-----
Segmentide koondstatistika

WITH segmentide_tabel AS (
    SELECT
        customer_id,
        SUM(total_price) AS kliendi_kogumuuk
    FROM sales
    GROUP BY customer_id
)
SELECT
    CASE
        WHEN kliendi_kogumuuk > 500 THEN 'VIP'
        WHEN kliendi_kogumuuk > 150 THEN 'Regular'
        ELSE 'Uus'
    END AS segment,
    COUNT(*) AS klientide_arv,
    ROUND(AVG(kliendi_kogumuuk), 2) AS keskmine_kaive
FROM segmentide_tabel
GROUP BY 1
ORDER BY keskmine_kaive DESC;








Kokkuvõte Annale, meil on 245 VIP-klienti, kes on meie brändi mootoriks!

Siin on peamised järeldused sinu turundusstrateegia jaoks:
VIP-kliendid: Need on peamiselt Tallinna elanikud, kes eelistavad kalleid naiste riideid ja eco-sertifitseeritud tooteid. Nad on Gold-tasemel ja toovad stabiilse käibe
.
Regular-segment: See on meie "kasvulava" Tartus ja Pärnus. Need kliendid on teinud vähemalt 2 ostu, kuid vajavad personaalset tõuget (nt tasuta tarne või lisaallahindlus), et liikuda VIP-staatusesse
.
Uued kliendid: Meil on suur hulk madala ostusagedusega kliente, kelle konverteerimine korduvostjateks on järgmise kvartali prioriteet
