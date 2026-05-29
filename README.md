# 🚕 Chicago Taxi Analysis — Cab Preferences & Weather Impact

Exploratory data analysis and hypothesis testing on Chicago taxi trip data, investigating company popularity, neighborhood demand, and the effect of weather conditions on trip duration.

---

## 📌 Overview

This project analyzes user preferences for taxi companies in Chicago and tests whether adverse weather conditions significantly affect trip duration from the Loop to O'Hare International Airport on Saturdays.

---

## 🎯 Analysis Tasks

| # | Task | Method |
|---|---|---|
| 1 | Top taxi companies by number of trips | Descriptive analysis + bar chart |
| 2 | Top dropoff neighborhoods | Descriptive analysis + bar chart |
| 3 | Weather impact on trip duration | Mann-Whitney U hypothesis test |

---

## 📊 Datasets

| File | Description | Records |
|---|---|---|
| `project_sql_result_01.csv` | Taxi companies and trip counts | 64 companies |
| `project_sql_result_04.csv` | Neighborhoods and average trips | 94 neighborhoods |
| `project_sql_result_07.csv` | Saturday trips with weather conditions | 1,068 records |

---

## 🔧 Methodology

### Exploratory Analysis
- Identified top 10 taxi companies by total trips
- Identified top 10 dropoff neighborhoods by average trip count
- Verified data quality: no missing values in files 01 and 04; 197 duplicates removed from file 07

### Hypothesis Test — Weather Impact on Trip Duration
- **H₀:** Trip duration distributions are equal under good and bad weather
- **H₁:** Trip duration distributions differ between weather conditions
- **Test:** Mann-Whitney U (two-sided) — chosen because data failed the Shapiro-Wilk normality test
- **Significance level:** α = 0.05

---

## 📈 Results

**Top 3 Taxi Companies:**

| Company | Trips |
|---|---|
| Flash Cab | 19,558 |
| Taxi Affiliation Services | 11,422 |
| Medallion Leasing | 10,367 |

**Top 3 Dropoff Neighborhoods:**

| Neighborhood | Avg. Trips |
|---|---|
| Loop | 10,727 |
| River North | 9,524 |
| Streeterville | 6,665 |

**Hypothesis Test:**

| Condition | Trips | Avg. Duration |
|---|---|---|
| Good weather | 723 | 2,032 seconds (~34 min) |
| Bad weather | 148 | 2,409 seconds (~40 min) |

- **U statistic:** 37,000.5 | **p-value:** < 0.0001
- **Conclusion:** Rejected H₀ — bad weather significantly increases trip duration ✅

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-lightgrey)
![SciPy](https://img.shields.io/badge/SciPy-Statistics-blue)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange)

- **Python** — Pandas, NumPy
- **Statistics** — SciPy (Shapiro-Wilk, Mann-Whitney U)
- **Visualization** — Matplotlib

---

## 📁 Project Structure

```
chicago-taxi-analysis/
│
├── S7.ipynb                        # Full analysis and hypothesis test
├── README.md
└── .gitignore
```

---

## 🚀 How to Run

```bash
# Clone the repository
git clone https://github.com/laaurasaporski/chicago-taxi-analysis.git

# Install dependencies
pip install pandas numpy scipy matplotlib

# Open the notebook
jupyter notebook S7.ipynb
```

---

## 💡 Key Insights

- **Flash Cab dominates** with nearly twice the trips of the second-place company
- **Loop and River North** are the most popular destinations, likely driven by business and tourism demand
- **Bad weather adds ~6 minutes** to average trip duration on the Loop → O'Hare route on Saturdays
- The Mann-Whitney U test was the appropriate choice given the non-normal distribution of trip durations
