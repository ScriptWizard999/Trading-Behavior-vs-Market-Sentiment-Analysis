# Trader Behavior vs. Market Sentiment

This project analyzes how trading behavior (profitability, volume, trades, fees) aligns or diverges from overall market sentiment (Fear vs. Greed).  
The aim is to uncover hidden signals that can inform smarter trading strategies.

---

## 📂 Project Structure
- `historical_data.csv` — Raw trade-level data from Hyperliquid  
- `fear_greed_index.csv` — Bitcoin Fear & Greed Index (2018–2025)  
- `notebook_1.ipynb` — Jupyter notebook with full analysis  
- `Data Science Assignment Report.pdf` —  project report  

⚠️ Note: The `historical_data.csv` file is not included in this repository due to size limits.  
Please download it separately from Google Drive before running the notebook:  

[Download historical_data.csv (Google Drive)](https://drive.google.com/file/d/1RSIUk6PH0yD2DSS7JlE2DjIaM3BAoNRF/view?usp=sharing)

Place the file in the `CSV_files/` folder of this repository to reproduce the results.


---

## ⚙️ Methodology

1. **Data Loading & Cleaning**
   - Loaded both datasets with Pandas.
   - Converted timestamps (epoch → UTC).
   - Created consistent `Date` column.

2. **Daily Aggregation**
   - Aggregated trade-level data into daily summaries:
     - `daily_pnl`: Total closed PnL
     - `daily_volume_usd`: Trade volume in USD
     - `daily_trades`: Number of trades
     - `avg_fee`: Average transaction fee

3. **Merging with Sentiment Data**
   - Joined daily stats with the Fear & Greed Index on `Date`.
   - Inner join → matched sentiment days.
   - Left join → retained all trading days (including missing sentiment).

4. **Exploratory Data Analysis (EDA)**
   - Correlation heatmap
   - Bar plots (PnL, volume, trades vs. sentiment classes)
   - Scatter plots (sentiment value vs. activity metrics)

5. **Insights & Conclusion**
   - Fear is strongly linked to spikes in activity and profits.
   - Greed/Neutral correspond to calm, low-activity days.
   - One unclassified anomaly (2025-06-15) showed high volume but modest profit.

---

## 📊 Key Findings
- **Negative correlation** between sentiment score and trading activity:
  - Lower sentiment (Fear) → higher volume, more trades, greater PnL.
- **Fear days** recorded the highest activity in the dataset.
- **Greed/Neutral days** were stable, clustered with low volume and trades.
- **Anomaly (2025-06-15):** High volume but moderate PnL; no sentiment classification available.

---

## 🚀 How to Run
1. Clone this repository.  
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn

