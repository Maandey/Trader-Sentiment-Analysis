###Trader Sentiment Analysis

### 1. Project Overview
This project analyzes over 200,000 anonymized crypto trades to determine if market sentiment (The "Fear & Greed Index") acts as a predictor for trader behavior and profitability.

**Hypothesis:** Do retail traders "buy the top" during Extreme Greed, leading to lower profitability compared to Fear periods?

### 2. Methodology
* **Data Processing:**
    * Merged high-frequency trade data with daily Sentiment Index values.
    * Performed Timezone Normalization (IST to UTC) to ensure accurate alignment.
    * Imputed missing sentiment values using a forward-fill method to preserve trade continuity.
* **Feature Engineering:**
    * Calculated **Win Rate** (Winning Trades / Total Trades).
    * Used **Position Size (USD)** as a proxy for "Risk Appetite" (in absence of explicit leverage data).
* **Modeling:**
    * Implemented **K-Means Clustering (k=3)** on normalized features (Frequency, Size, Win Rate) to segment the user base into behavioral archetypes.

### 3. Key Insights 💡
The analysis revealed three critical patterns:

1.  **The "Greed Trap":**
    * During **"Extreme Greed" (Index > 75)**, the median Position Size increases by **~15%**, yet the median PnL remains flat or declines. This indicates that traders take outsized risks during market euphoria without a corresponding edge.
2.  **Smart Money in Fear:**
    * "Fear" periods (Index < 25) show lower overall trading volume, but a **higher stability in median PnL**. This suggests that inexperienced "tourists" leave the market, leaving only disciplined traders active.
3.  **Trader Segmentation (Clustering Results):**
    * **Cluster 0 (The Scalpers):** High frequency, small position sizes, consistent small wins.
    * **Cluster 1 (The Whales):** Top 1% of position sizes, low frequency, high impact on PnL.
    * **Cluster 2 (The Churners):** High frequency, large sizing, but negative PnL—likely "revenge trading."

### 4. Strategy Recommendations 📈
Based on these data-driven insights, I propose two rules for an algorithmic trading strategy:

* **Rule A: The "Volatility Brake" (Risk Management)**
    * *Logic:* Since risk-taking spikes during Greed without higher returns.
    * *Action:* **Cap Maximum Position Size to 80%** of normal limits when Sentiment Index > 75. This prevents "blow-up" events during market tops.
* **Rule B: The "Contrarian Accumulation" (Alpha Gen)**
    * *Logic:* Win rates normalize during Fear periods.
    * *Action:* Increase capital allocation by **10%** for mean-reversion strategies when Sentiment Index < 20 (Extreme Fear).

---

### 5. Setup & Execution
To reproduce this analysis:

1.  **Clone the repo:**
    ```bash
    git clone [https://github.com/](https://github.com/Maandey/Trader-Sentiment-Analysis.git)
    cd Trader-Sentiment-Analysis
    ```
2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```
3.  **Run the Notebook:**
    ```bash
    jupyter notebook notebooks/analysis_and_Modeling.ipynb
    ```

**Dependencies:**
* `pandas` (Data Manipulation)
* `seaborn` & `matplotlib` (Visualization)
* `scikit-learn` (K-Means Clustering)
