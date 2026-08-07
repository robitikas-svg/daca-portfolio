
--- PUHASTUSRAPORT ---
Algne ridade arv: 15234
Eemaldatud duplikaate (invoice_id): 4291
Eemaldatud erindeid (total_price): 556
Õige andmevahemik: 2023-01-01 00:00:00 kuni 2026-06-28 00:00:00
Lõplik ridade arv (valmis RFM jaoks): 8621

Parandatud ja puhastatud fail 'df_cleaned_roll_B.csv' edukalt eksporditud!


# Nädal 7: grupitöö:

1.Duplikaatide eemaldamine:

import pandas as pd

--# 1. Lae andmed
df = pd.read_csv('df_merged_roll_A_loplik.csv')
initial_rows = len(df)

--# 2. Eemalda puuduvate väärtustega read (Liisi nõue)
df = df.dropna(subset=['customer_id', 'sale_date', 'total_price']).copy()

--# 3. Jäta alles vaid positiivsed tehingusummad (Liisi nõue)
df = df[df['total_price'] > 0].copy()

--# 4. Eemalda duplikaadid (invoice_id järgi)
duplicate_count = df.duplicated(subset=['invoice_id']).sum()
df_dedup = df.drop_duplicates(subset=['invoice_id']).copy()

--# 5. Parsi kuupäevad täpse suunamisega (DD/MM/YYYY ja YYYY-MM-DD)
df_dedup['sale_date'] = pd.to_datetime(df_dedup['sale_date'], format='%d/%m/%Y', errors='coerce').fillna(
pd.to_datetime(df_dedup['sale_date'], format='%Y-%m-%d', errors='coerce')
)

--# 6. Eemalda erindid tehingu kogusumma ('total_price') järgi (IQR meetod)
Q1 = df_dedup['total_price'].quantile(0.25)
Q3 = df_dedup['total_price'].quantile(0.75)
IQR = Q3 - Q1

df_cleaned = df_dedup[(df_dedup['total_price'] >= (Q1 - 1.5 * IQR)) & (df_dedup['total_price'] <= (Q3 + 1.5 * IQR))].copy()
outliers_count = len(df_dedup) - len(df_cleaned)

--# 7. Lõplik puhastusraport
print("--- PUHASTUSRAPORT ---")
print(f"Algne ridade arv: {initial_rows}")
print(f"Eemaldatud duplikaate (invoice_id): {duplicate_count}")
print(f"Eemaldatud erindeid (total_price): {outliers_count}")
print(f"Õige andmevahemik: {df_cleaned['sale_date'].min()} kuni {df_cleaned['sale_date'].max()}")
print(f"Lõplik ridade arv (valmis RFM jaoks): {len(df_cleaned)}")

--# 8. Eksport uuesti
df_cleaned.to_csv('df_cleaned_roll_B.csv', index=False)
print("\nParandatud ja puhastatud fail 'df_cleaned_roll_B.csv' edukalt eksporditud!")
