---Päring, mis ühendab sales ja products tabelid, et näha tootenimesid koos müüdud kogustega.

SELECT 
    p.product_name, 
    p.category, 
    s.quantity, 
    s.unit_price
FROM sales s
JOIN products p ON s.product_id = p.product_id
ORDER BY s.quantity DESC
LIMIT 15;# Nädal 3: SQL Basics

---Tooted mida ei ole kunagi müüdud
SELECT 
    p.product_name, 
    p.category, 
    p.retail_price
FROM products p
LEFT JOIN sales s ON p.product_id = s.product_id
WHERE s.sale_id IS NULL;


---Millised tootekategooriad müüvad igas linnas kõige rohkem
SELECT 
    c.city AS linn, 
    p.category AS kategooria, 
    SUM(s.total_price) AS kogumuuk
FROM sales s
JOIN customers c ON s.customer_id = c.customer_id
JOIN products p ON s.product_id = p.product_id
GROUP BY c.city, p.category
ORDER BY kogumuuk DESC;


---Ühenda sales, customers ja products. Grupeeri kliendi ja kategooria kaupa. Näita: klient, linn, kategooria, kogumüük.
SELECT 
    c.first_name || ' ' || c.last_name AS klient, 
    c.city AS linn, 
    p.category AS kategooria, 
    SUM(s.total_price) AS kogumuuk
FROM sales s
JOIN customers c ON s.customer_id = c.customer_id
JOIN products p ON s.product_id = p.product_id
GROUP BY c.first_name, c.last_name, c.city, p.category
ORDER BY kogumuuk DESC
LIMIT 20;


---Kadunud kliendid linnade kaupa
SELECT 
    c.city AS linn, 
    COUNT(c.customer_id) AS kadunud_kliente
FROM customers c
LEFT JOIN sales s ON c.customer_id = s.customer_id
WHERE s.sale_id IS NULL
GROUP BY c.city
ORDER BY kadunud_kliente DESC;


---Müümata tooted kategooriate kaupa
SELECT 
    p.category AS kategooria, 
    COUNT(p.product_id) AS muumata_toodete_arv
FROM products p
LEFT JOIN sales s ON p.product_id = s.product_id
WHERE s.sale_id IS NULL
GROUP BY p.category
ORDER BY muumata_toodete_arv DESC;


---
