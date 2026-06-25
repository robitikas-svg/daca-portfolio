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



UrbanStyle kasutab kahekanalilist (dual-channel) lähenemist, kombineerides e-kaubanduse ja füüsiliste kaupluste eeliseid
E-pood (urbanstyle.ee): See on meie peamine tulukanal, moodustades ligikaudu 60% ettevõtte kogukäibest Veebimüük tagab kättesaadavuse üle Eesti 24/7
Füüsilised kauplused: Poed toovad umbes 40% käibest ning asuvad kolmes strateegilises asukohas: Tallinnas (Rotermanni kvartal), Tartus (Tasku keskus) ja Pärnus (Port Artur)
Maksevõimalused: Pakume klientidele paindlikke ja turvalisi lahendusi:
Pangakaardimaksed nii veebis kui ka kauplustes.
Sularahamakse võimalus füüsilistes poodides.
Järelmaks, mis võimaldab suuremaid oste ajas hajutada ja muudab kvaliteetse moe kättesaadavamaks.
Andmete omapära: Oluline on arvestada, et veebipoe müügiandmetes puudub asukohainfo (andmebaasis märgitud kui NULL)
See on äriliselt loogiline, kuna e-poe tehingud ei ole seotud konkreetse füüsilise kauplusega
