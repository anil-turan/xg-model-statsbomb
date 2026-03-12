# ⚽ Expected Goals (xG) Model — StatsBomb Open Data

A logistic regression xG model built on StatsBomb's free La Liga 2015/16 event data.
Combines football domain knowledge with data science to quantify shot quality.

## What is xG?

Expected Goals (xG) is a metric that estimates the probability of a shot resulting in a goal based on the characteristics of that shot — primarily where it was taken from and how.
A shot with xG = 0.25 is expected to result in a goal 25% of the time.

## Project Structure

```
xg-model-statsbomb/
├── xg_model_statsbomb.ipynb   # Main notebook (EDA → model → evaluation)
├── requirements.txt
└── README.md
```

## Pipeline

```
StatsBomb API → Shot Events → Feature Engineering → Logistic Regression → Evaluation & Visualisation
```

| Step | Description |
|------|-------------|
| **Data** | StatsBomb open data — La Liga 2015/16 (~380 matches) |
| **Features** | Distance, shot angle, header, open play flag |
| **Model** | Logistic Regression (sklearn) |
| **Evaluation** | ROC-AUC, Brier Score, Calibration Curve |
| **Output** | Shot maps, player xG leaderboard |

## Features Used

| Feature | Description |
|---------|-------------|
| `distance` | Euclidean distance from shot location to goal centre |
| `angle` | Angle subtended by goal mouth at shot location |
| `is_header` | 1 if headed shot, 0 otherwise |
| `is_open_play` | 1 if open play, 0 if set piece / counter |

## Key Visualisations

- **Shot Map** — all shots coloured by outcome
- **Goal Rate by Distance** — shows the distance-xG relationship
- **ROC Curve + Calibration Curve** — model quality assessment
- **xG Shot Map** — bubble size & colour proportional to predicted xG
- **Player Goals vs xG** — who overperformed / underperformed?

## Installation

```bash
git clone https://github.com/anilturan/xg-model-statsbomb
cd xg-model-statsbomb
pip install -r requirements.txt
jupyter notebook xg_model_statsbomb.ipynb
```

## Requirements

```
statsbombpy>=1.16.0
pandas>=1.5.3
numpy>=1.26.4
scikit-learn>=1.3.0
matplotlib>=3.7.0
seaborn>=0.12.0
```

## Data

All data is sourced from [StatsBomb Open Data](https://github.com/statsbomb/open-data) — freely available for personal and research use.

## Possible Extensions

- Add **shot pressure** from StatsBomb freeze frame data
- **XGBoost / Random Forest** for non-linear capture
- Extend to multiple leagues / seasons
- Interactive **Plotly** shot maps

---

*Built as part of a football analytics portfolio. Data courtesy of StatsBomb.*
