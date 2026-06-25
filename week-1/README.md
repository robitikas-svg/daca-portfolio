1: SELECT channel, store_location, payment_method
FROM sales
LIMIT 10;

2: SELECT DISTINCT channel FROM sales;

3: SELECT DISTINCT store_location FROM sales;

4: SELECT DISTINCT payment_method FROM sales;

5: SELECT * FROM sales
WHERE channel = 'online'
ORDER BY total_price DESC
LIMIT 15;

6: SELECT COUNT(*) AS puuduv_asukoht
FROM sales
WHERE store_location IS NULL;
