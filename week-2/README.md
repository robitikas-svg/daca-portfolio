# Nädal 2: SQL Basics

[x] Kõigi rollide (A–D) väljundid on üle vaadatud Kontrollisin üle müügiandmete puhastamise (Roll A), kliendiandmete analüüsi (Roll B), tooteandmete kvaliteedi (Roll C) ning müügikanalite mustrid (Roll D)
Kõik meeskonnaliikmed on oma osa esitanud ning need moodustavad ühtse terviku.
[x] Ristkontroll tehtud — numbrid klapivad omavahel Ristkontroll kinnitas järgmist: toorandmetes on 15 234 rida, kuid unikaalseid arveid on vaid 10 118
See tähendab, et 5 116 rida on duplikaadid, mis tuleb eemaldada, et mitte moonutada käibeandmeid. Kui kustutame andmebaasist 5 116 rida siis see teeb korda ka andmebaasis olevad 4013 korduvat arvet
Samuti klapib 1 487 NULL väärtusega tehingu arv kliendiandmete puudulikkusega
[x] Valideerimisraport kirjas (leiud + paranduskohad)
Kriitiline leid: 33,6% müügiandmetest on duplikaadid
Kvaliteediviga: 1 487 kliendikirjel puudub customer_id
Andmeviga: Tuvastati kuupäevi, mis on varasemad kui UrbanStyle'i asutamine 2020. aasta kevadel
Parandus: Kõik duplikaadid on testtabelis märgistatud ja eemaldatavad, NULL väärtused on asendatud "Unknown Customer" tähisega
[x] Ühtne ärisoovitus stakeholderile (Toomas) on koostatud Ärikokkuvõte: UrbanStyle'i andmekaos on hallatav, kuid nõuab kohest tegutsemist enne investorite kohtumist
Peamine järeldus on, et e-pood (60% käibest) on ettevõtte mootor, kuid selle andmete kogumine on ebakvaliteetne, mis takistab turunduse personaliseerimist
