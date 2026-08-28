**Junior Data Analyst | SQL, Python, Power BI | Turning Data into Business Insights

📧[Email](Robi.tikas@gmail.com)    🔗[LinkedIn](https://www.linkedin.com/in/robi-tikas-57748a239/) 
    💼[Portfolio/GitHub](https://github.com/robitikas-svg/daca-portfolio)
 
 **Asukoht**: Eesti



# Sissejuhatus ja ärikontekst
Olen edukalt läbinud intensiivse 11-nädalase andmeanalüütiku kiirendiprogrammi DACA (Data Analyst Career Accelerator), mis on loodud spetsiaalselt karjäärivahetajatele
. Selle praktilise teekonna jooksul ei lahendanud ma pelgalt teoreetilisi harjutusi, vaid töötasin reaalsete andmetega simulatsioonifirmas UrbanStyle.ltd (Eesti jätkusuutlik jaekaubanduse ja moeettevõte, millel on e-pood ja kolm füüsilist poodi Tallinnas, Tartus ja Pärnus)
.
Minu peamiseks eesmärgiks oli aidata tegevjuht Kristi Tammel andmekaosest luua usaldusväärne, automatiseeritud analüütika ja interaktiivsed dashboard'id, et esitleda investoritele andmepõhist äriplaani 500 000 euro suuruse kasvurahastuse kaasamiseks






# Minu tehnilised oskused (Technical Stack)

**Andmebaasid ja päringukeeled**: SQL (PostgreSQL, pilveplatvorm Supabase)
.

**Andmetöötlus ja koodipõhine analüüs**: Python (pandas ja numpy teegid, Jupyter Notebooks)
.

**Visualiseerimine ja ärianalüütika (BI)**: Power BI (Track A) või Plotly + Streamlit (Track B), Miro kollaboratsioonitööriist
.

**Versioonihaldus ja meeskonnatöö**: Git ja GitHub
.

**Automatiseerimine ja süsteemid**: Supabase API, ETL-pipeline'id, veakäsitlus, logimine ja GitHub Actions




# Mida ma tegin ja õppisin (DACA õpiteekond)
1. **Andmebaasid, uurimine ja andmekvaliteedi parandamine (Shu-faas)**
Tegevused: Alustasin oma professionaalse töökeskkonna seadistamisega ja asusin lahendama IT-direktor Toomas Kaski tuvastatud andmekaost
. Uurisin UrbanStyle’i tooreid müügiandmeid (sales), kust leidsin tõsiseid andmekvaliteedi probleeme
.
Õppetunnid: Õppisin kirjutama korrektseid ja optimeeritud SQL-päringuid (kasutades käske SELECT, WHERE, ORDER BY, LIMIT, DISTINCT, COUNT)
. Tuvastasin, et müügitehingute andmebaasi 15 234 reast olid tervelt 5 116 duplikaadid (u 33,6% andmetest), mis moonutasid käivet
. Õppisin andmeid puhastama "kirurgiliselt, mitte pommiga"
. Lõin andmebaasist turvalise testkoopia, eemaldasin duplikaadid aknafunktsioonide (ROW_NUMBER()) abil, täitsin puuduvad kliendinimed (COALESCE funktsiooniga), valideerisin tuleviku kuupäevad ning ühtlustasin linnade kirjapildid
. Kõik sammud dokumenteerisin turvaliste transaktsioonide (BEGIN, COMMIT, ROLLBACK) ja audit logi abil
.
2. **Ärianalüüs ja andmete seostamine (Shu-Ha üleminek)**
Tegevused: Ühendasin eraldiseisvad müügi-, kliendi- ja tootetabelid, et vastata turundusjuht Anna Metsa kriitilistele küsimustele
.
Õppetunnid: Sain selgeks SQL-i liitmiste (INNER JOIN, LEFT JOIN, FULL OUTER JOIN) loogika ning oskuse leida "kadunud andmeid" ehk kliente, kes registreerusid, kuid pole kunagi ostnud
. Kasutasin täpsemat andmete koondamist (GROUP BY, HAVING) ja ajutisi tabeleid (CTE-d), et arvutada äri jaoks võtmetähtsusega KPI-sid, nagu keskmist tellimusväärtust (AOV) ja kliendi eluea väärtust (CLV)
.
3. **Visualiseerimine, disain ja andmete jutustamine (Ha-faas)**
Tegevused: Disainisin ja ehitasin interaktiivse dashboard'i, mis vastab tegevjuht Kristi vajadustele ja aitab andmeid reaalajas uurida
.
Õppetunnid: Rakendasid Cole Nussbaumer Knaflici ("Storytelling with Data") põhimõtteid
. Õppisin eemaldama visuaalset müra (andmete-tindi suhte optimeerimine) ja disainima dashboard'i vastavalt inimsilma liikumisele (F-muster)
. Tõin esile olulisimad KPI-kaardid (käive, kliendid, AOV), lisasin müügitrendi joondiagrammile annotatsioonid (nt Black Friday mõju) ja eesmärgijooned ning disainisin eraldi taktilise operatsioonide vaate operatsioonijuht Liis Koppelile (reaalajas madalad laoseisud ja poodide võrdlus)
.
4. **Keeruline kliendianalüüs Pythonis ja Pandas**
Tegevused: Kuna SQL-i võimekus keeruliste ärisegmentide ja kvintiilide arvutamisel on piiratud, liikusin koodipõhise analüüsi juurde ja teostasin tootehaldur Marko Saarele täieliku RFM-analüüsi (Recency, Frequency, Monetary)
.
Õppetunnid: Õppisin kasutama Pythonit ja pandas DataFrame-i loogikat
. Grupeerisin kliendid nende ostuajaloo värskuse, sageduse ja rahalise väärtuse alusel, kasutades pandas-e qcut() funktsiooni
. Segmentisin kliendid 5 gruppi (VIP Champions, Loyal Customers, Potential Loyalists, At Risk, Lost) ja pakkusin Markole välja konkreetsed, mõõdetavad kampaaniasoovitused
. Eksportisin tulemused turunduse jaoks puhtas ja GDPR-sõbralikus CSV-vormingus
.
5. **API-d ja andmetorude automatiseerimine (Ri-faas)**
Tegevused: Ehitasin staatilisest analüüsist dünaamilise ja korduva tootmisvalmis süsteemi, luues täisautomaatse andmetoru
.
Õppetunnid: Õppisin ühenduma Supabase andmebaasiga otse läbi Supabase Python SDK (REST API)
. Ehitasin modulaarse ETL (Extract-Transform-Load) pipeline'i, mis tõmbab igal käivitusel värsked andmed, puhastab need, teostab RFM-analüüsi ning salvestab tulemused
. Rakendasin professionaalset veakäsitlust (try-except koos exponential backoff retry-loogikaga), struktureeritud logimist (logging moodul) ja parameetritest juhitavat konfiguratsiooni (YAML)
. Töövoo ajastasin automaatselt GitHub Actions abil iga esmaspäeva hommikuks
.
6. **Karjääri ettevalmistus ja värbamine**
Tegevused & Õppetunnid: Vaatasin turgu tööandja silmade läbi
. Aitasin Liis Koppelil koostada andmeosakonna laienemise raames värbamisjuhendi 7 uue andmeanalüütiku palkamiseks (sh tehniliste oskuste hindamine, portfoolio audit, onboarding-plaanid)
. Tõlkisin oma DACA oskused kvantifitseeritud ja äriliselt tähendusrikkasse keelde ning õppisin koostama STAR-meetodil põhinevaid intervjuuvastuseid
.



# Kokkuvõtteks


**Minu loodud andmelahendused ei olnud pelgalt tehnilised harjutused, vaid neil oli reaalne äriline mõju**:

**VIP-klientide tuvastamine**: Tuvastasin andmetest 245 VIP-klienti, kes on brändi mootoriks ja genereerivad ebaproportsionaalselt suure osa käibest


**Aja kokkuhoid**: Säästsin meeskonna käsitööd u 4 tundi nädalas (üle 200 tunni aastas), automatiseerides iganädalase kliendisegmenteerimise


**Kadude ennetamine**: Lõin Liisile KPI-monitooringu, mis tuvastas Tartu poe varude anomaaliad, hoides ära potentsiaalsed müügikaotused


**Turunduse optimeerimine**: Tõestasin Anna kampaaniate põhjal Facebook-müügi 3.2x ROI (tasuvuse), mis aitas Kristil kindlustada investorite usalduse


See terviklik kogemus on teinud minust mitmekülgse juunior-andmeanalüütiku, kes suudab astuda andmekaosest andmepõhiste strateegiliste otsuste ja tootmiskõlbliku automatiseerimiseni.
