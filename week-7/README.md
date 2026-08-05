--- PUHASTUSRAPORT ---
Algne ridade arv: 15234
Eemaldatud duplikaate (invoice_id): 5116
Eemaldatud erindeid (total_price): 677
Õige andmevahemik: 2023-01-01 00:00:00 kuni 2026-06-28 00:00:00
Lõplik ridade arv (valmis RFM jaoks): 9441

Parandatud fail 'df_cleaned_roll_B.csv' edukalt eksporditud!




# Nädal 7: grupitöö:

1.Duplikaatide eemaldamine:

import pandas as pd

# 1. Lae andmed
df = pd.read_csv('df_merged_roll_A_loplik.csv')
initial_rows = len(df)

# 2. Eemalda duplikaadid (kogu rea põhjal)
duplicate_count = df.duplicated().sum()
df_dedup = df.drop_duplicates().copy()

# 3. Leia esimene arvuline veerg (mis pole ID) erindite eemaldamiseks
num_cols = df_dedup.select_dtypes(include=['number']).columns
target_num_col = [c for c in num_cols if 'id' not in c.lower()][0]

# 4. Outlier'ite eemaldamine (IQR meetod)
Q1 = df_dedup[target_num_col].quantile(0.25)
Q3 = df_dedup[target_num_col].quantile(0.75)
IQR = Q3 - Q1

df_cleaned = df_dedup[(df_dedup[target_num_col] >= (Q1 - 1.5 * IQR)) & (df_dedup[target_num_col] <= (Q3 + 1.5 * IQR))].copy()
outliers_count = len(df_dedup) - len(df_cleaned)

# 5. Puhastusraport ja väljund
print("Esialgne kuju:", df.shape)
print("Eemaldatud duplikaate:", duplicate_count)
print("\nNULL väärtused:")
print(df_dedup.isnull().sum())

print("\n--- PUHASTUSRAPORT ---")
print(f"Algne ridade arv: {initial_rows}")
print(f"Eemaldatud duplikaate: {duplicate_count}")
print(f"Eemaldatud erindeid ({target_num_col}): {outliers_count}")
print(f"Lõplik ridade arv (valmis RFM jaoks): {len(df_cleaned)}")

# 6. Salvesta tulemus
df_cleaned.to_csv('df_cleaned_roll_B.csv', index=False)
print("\nSalvestatud faili 'df_cleaned_roll_B.csv'!")


2. Lõpplik puhastus:

import pandas as pd

# 1. Lae andmed
df = pd.read_csv('df_merged_roll_A_loplik.csv')
initial_rows = len(df)

# 2. Eemalda duplikaadid (invoice_id järgi)
duplicate_count = df.duplicated(subset=['invoice_id']).sum()
df_dedup = df.drop_duplicates(subset=['invoice_id']).copy()

# 3. Parsi kuupäevad segavormingu/päev-enne-tugi abil
df_dedup['sale_date'] = pd.to_datetime(df_dedup['sale_date'], format='mixed', dayfirst=True)

# 4. Eemalda erindid tehingu kogusumma ('total_price') järgi (IQR meetod)
Q1 = df_dedup['total_price'].quantile(0.25)
Q3 = df_dedup['total_price'].quantile(0.75)
IQR = Q3 - Q1

df_cleaned = df_dedup[(df_dedup['total_price'] >= (Q1 - 1.5 * IQR)) & (df_dedup['total_price'] <= (Q3 + 1.5 * IQR))].copy()
outliers_count = len(df_dedup) - len(df_cleaned)

# 5. Lõplik puhastusraport
print("--- PUHASTUSRAPORT ---")
print(f"Algne ridade arv: {initial_rows}")
print(f"Eemaldatud duplikaate (invoice_id): {duplicate_count}")
print(f"Eemaldatud erindeid (total_price): {outliers_count}")
print(f"Andmevahemik: {df_cleaned['sale_date'].min()} kuni {df_cleaned['sale_date'].max()}")
print(f"Lõplik ridade arv (valmis RFM jaoks): {len(df_cleaned)}")

# 6. Salvesta puhastatud fail
df_cleaned.to_csv('df_cleaned_roll_B.csv', index=False)
print("\nSalvestatud lõplik fail 'df_cleaned_roll_B.csv'!")
