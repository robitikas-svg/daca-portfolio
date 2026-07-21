
-----Müügi kaupliste lõikes
SELECT
store_location,
SUM(total_price) AS tulu,
COUNT(*) AS tehinguid
FROM sales
GROUP BY store_location
ORDER BY tulu DESC;

----Laoseisude jaotus tootekategooriate kaupa

SELECT
p.category,
SUM(i.quantity_available) AS kogus
FROM inventory i
JOIN products p ON i.product_id = p.product_id
WHERE i.quantity_available > 0
GROUP BY p.category
ORDER BY kogus DESC;


Liis, Tallinn moodustab 37% müügist. Laoseisud näitavad, et meeste riiete kategoorias on hetkel suurim kapitali seotus, kuid aksessuaaride varud on müügimahuga võrreldes kriitiliselt madalad ning Tartu poe andmed vajavad tuvastatud ebakõlade tõttu kohest füüsilist ülekontrolli

