# Nädal 2: SQL Basics

1.E-mailide duplikaat

WITH numbered_customers AS (
    SELECT 
        customer_id, 
        email, 
        ROW_NUMBER() OVER (PARTITION BY email ORDER BY customer_id ASC) AS rn
    FROM customers
    WHERE email IS NOT NULL
)
SELECT * FROM numbered_customers WHERE rn > 1;

2. Duplikaatide audit

SELECT 
    COUNT(*) AS ridu_kokku, 
    COUNT(DISTINCT product_name) AS unikaalseid_tooteid
FROM products;

3. COALESCE funktsiooni

SELECT 
    COALESCE(first_name, 'Tundmatu') AS eesnimi, 
    COALESCE(last_name, '') AS perekonnanimi,
    COALESCE(email, 'E-mail puudub') AS email,
    COALESCE(phone, 'Telefon puudub') AS telefon,
    city
FROM customers
-- Filtreerime välja ainult need kliendid, kellel on vähemalt üks kriitiline väli täitmata
WHERE first_name IS NULL 
   OR last_name IS NULL 
   OR email IS NULL 
   OR phone IS NULL;



4. Customers tabeli linnade "puhastatud" versiooni
SELECT 
    INITCAP(TRIM(city)) AS puhastatud_linn,
    COUNT(*) AS kliente_kokku,
    COUNT(DISTINCT city) AS algseid_kirjaviise
FROM customers
-- Grupeerime puhastatud nime järgi, et ühendada väärtused nagu 'tallinn' ja ' TALLINN '
GROUP BY puhastatud_linn
-- Sorteerime klientide arvu järgi kahanevalt



   
ORDER BY kliente_kokku DESC;
