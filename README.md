Project Overview

This project explores how user sentiment toward Spotify changes over time. Reviews and engagement metrics are converted into a sentiment time series, and we model its evolution to detect trends and forecast future values. The insights aim to trigger early retention strategies and improve user satisfaction.

Motivation

Treating reviews as isolated events ignores temporal patterns that reveal shifts in user experience.

Detecting sentiment transitions early can reduce churn and enhance retention.

Platforms like Spotify can benefit from proactive, data-driven decisions about features, customer service, and loyalty programs.

Dataset

reviewId / ID — unique identifier for each review

userName / reviewer — name or label of reviewer (e.g. “A Google user”)

content / review — textual review

score / rating — user rating (e.g. 1–5)

thumbsUpCount / likes — the count of “likes” given to the review

reviewCreatedVersion / app version — Spotify app version when review submitted

at / date of review — timestamp or date of the review

Time span: September 2018 → May 2024
Missing data & skewness: About 7% missing app version; likes are heavily skewed

Methodology

Sentiment Extraction — use RoBERTa to derive sentiment scores from review text and incorporate engagement metrics.

Time Series Construction — structure the scores in chronological order to form 
𝑆
(
𝑡
)
=
{
𝑠
1
,
𝑠
2
,
…
 
}
S(t)={s
1
	​

,s
2
	​

,…}.

Trend & Pattern Detection — analyze seasonal, cyclic, and abrupt shifts in sentiment.

Forecasting — predict future sentiment values for horizons 
ℎ
>
0
h>0.

Evaluation & Analysis — compare models using MAE, RMSE, MAPE, and qualitatively interpret sentiment shifts.

Experiments & Models

We experiment with several models, including:

Moving Averages & Seasonal Decomposition

ARIMA / SARIMA

Recurrent Models: LSTM, GRU

Transformer / Temporal Attention Networks

State-Space Models & Hybrid Approaches

Baselines (e.g. naive forecast, simple average)

Results

Model	MSE	MAE	RMSE 

BiLSTM	0.0090	0.0728	0.0946

Transformer	0.0073	0.0642	0.0852

N-BEATS	0.0069	0.0629	0.0832

TCN	0.0088	0.0713	0.0937

Moving Average	0.0067	0.0608	0.0821

Insights:

The Moving Average baseline outperformed many complex models, suggesting sentiment series may be relatively smooth or predictable.

N-BEATS yielded the best performance among trained models.

Further work is needed to capture abrupt sentiment shifts and rare events.
