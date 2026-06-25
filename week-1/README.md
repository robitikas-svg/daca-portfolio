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



-Kahekanaliline lähenemine: UrbanStyle kasutab nii e-poodi kui ka füüsilisi kauplusi, et jõuda oma sihtrühmani
E-pood (urbanstyle.ee): See on ettevõtte põhiline tulukanal, mis moodustab umbes 60% käibest
-Füüsilised kauplused: Poed toovad ligikaudu 40% käibest, meie poed asuvad Tallinnas. Tartus ja Pärnus.

Klientidele on võimaldatud turvalisi pangakaardimakseid nii veebis kui kauplustes, sularahamakse võimalust füüsilistes asukohtades ning paindlikku järelmaksu
