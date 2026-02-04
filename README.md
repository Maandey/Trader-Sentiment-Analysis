### Trader Behavior Analysis: Fear vs. Greed

### 1. Executive Summary We analyzed 200k+ trades to determine if Bitcoin market sentiment predicts trader performance. Contrary to the "Crowd Wisdom" hypothesis, our data suggests that Extreme Greed correlates with higher risk-taking (Position Size) but diminishing returns (lower Median PnL).

### 2. Key Insights

The "Greed Trap": During "Extreme Greed" days, median position size increases by ~15%, yet the Win Rate drops. This suggests retail traders "FOMO" into tops.

Smart Money in Fear: "Fear" days show lower volume but higher consistency in PnL, indicating only experienced traders are active.

Segmentation: Clustering revealed 3 distinct groups:

Cluster 0: High-Freq / Low Size (Scalpers)

Cluster 1: Low-Freq / Massive Size (Whales)

Cluster 2: Inconsistent / High Risk (Gamblers)

### 3. Strategy Recommendation

Algo Rule: Reduce max position size cap by 20% when Sentiment Index > 75 (Extreme Greed) to protect against volatility flushes.
