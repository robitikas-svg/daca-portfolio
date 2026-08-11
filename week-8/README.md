Grupitöö Roll c

import os
from datetime import datetime
import pandas as pd
import plotly.express as px
import plotly.graph_objects as go


# 1. Funktsioon nädalaste tululiikumiste joondiagrammi loomiseks
def create_weekly_chart(df_weekly):
    if df_weekly is None or df_weekly.empty:
        return None
    fig = px.line(
        df_weekly,
        x='week',
        y='revenue',
        title='Nädala tulu'
    )
    return fig


# 2. Funktsioon KPI indikaatorite kaardi/koondvaate loomiseks
def create_kpi_summary(kpis):
    if not kpis:
        return None
    fig = go.Figure()
    
    # Lisame esimese indikaatori (Total Revenue)
    fig.add_trace(go.Indicator(
        mode="number",
        value=kpis.get('total_revenue', 0),
        title={"text": "Total Revenue (€)"},
        domain={'row': 0, 'column': 0}
    ))
    
    # Lisame teise indikaatori (Customer Count)
    fig.add_trace(go.Indicator(
        mode="number",
        value=kpis.get('customer_count', 0),
        title={"text": "Customer Count"},
        domain={'row': 0, 'column': 1}
    ))
    
    # Lisame kolmanda indikaatori (Avg Order Value)
    fig.add_trace(go.Indicator(
        mode="number",
        value=kpis.get('avg_order_value', 0),
        title={"text": "Avg Order Value (€)"},
        domain={'row': 0, 'column': 2}
    ))
    
    fig.update_layout(
        grid={'rows': 1, 'columns': 3, 'pattern': 'independent'},
        title_text="Peamised KPI-d"
    )
    return fig


# 3. Funktsioon tulemuste eksportimiseks (CSV + HTML)
def export_results(df, output_dir='output', fig_weekly=None, fig_kpi=None):
    # Loo output/ kaust, kui seda ei eksisteeri
    os.makedirs(output_dir, exist_ok=True)
    
    # Salvesta CSV ajatempliga failinimega (nt rfm_20260811.csv)
    date_str = datetime.now().strftime("%Y%m%d")
    csv_filename = f"rfm_{date_str}.csv"
    csv_path = os.path.join(output_dir, csv_filename)
    
    if df is not None:
        df.to_csv(csv_path, index=False)
        print(f"CSV fail edukalt salvestatud: {csv_path}")
    
    # Salvesta diagrammid HTML-ina
    if fig_weekly is not None:
        html_weekly = os.path.join(output_dir, 'weekly_revenue.html')
        fig_weekly.write_html(html_weekly)
        print(f"Joondiagramm salvestatud: {html_weekly}")
        
    if fig_kpi is not None:
        html_kpi = os.path.join(output_dir, 'kpi_summary.html')
        fig_kpi.write_html(html_kpi)
        print(f"KPI diagramm salvestatud: {html_kpi}")


# 4. Testimine näidisandmetega
if __name__ == '__main__':
    df_weekly_test = pd.DataFrame({
        'week': ['Nädal 1', 'Nädal 2'],
        'revenue': [1200, 1800]
    })
    
    kpis_test = {
        'total_revenue': 3000,
        'customer_count': 25,
        'avg_order_value': 120
    }
    
    df_rfm_test = pd.DataFrame({
        'customer_id': [1, 2],
        'rfm_score': [555, 444]
    })
    
    chart1 = create_weekly_chart(df_weekly_test)
    chart2 = create_kpi_summary(kpis_test)
    
    export_results(
        df=df_rfm_test,
        output_dir='output',
        fig_weekly=chart1,
        fig_kpi=chart2
    )
