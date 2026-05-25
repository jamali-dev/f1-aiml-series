# 🏎️ F1 AI/ML Series
### Learning AI/ML through Formula 1 Data

A multi-part project series that uses real F1 telemetry data to build 
progressively complex AI/ML projects — from data analysis to race 
prediction to AI race engineers.

---

## Part 2 — The Pit Wall 🏁

### What I Built
A data analysis pipeline using the FastF1 API to analyse the 
2026 Australian Grand Prix. The notebook covers lap time progression, 
gap to leader calculations, tyre strategy visualisation, and ERS 
mode detection through Speed vs RPM telemetry.

### Key Findings
- VER and NOR set the fastest individual laps but the race was won 
  by Russell and Antonelli — proving that tyre management and strategy 
  matter more than raw pace over a full race distance.
- Lap times were slowest in the opening phase due to heavy fuel load, 
  cold tyres, and close racing in traffic. Pace improved consistently 
  as fuel burned off and drivers spaced out.
- Mercedes executed a perfect undercut — pitting earlier than Ferrari 
  to emerge on fresh tyres with clean air, building a 1-2 finish in 
  the pit lane rather than on track.
- ERS recharge zones map directly onto braking zones, with boost 
  deployment visible on every straight — the energy cycle of an F1 
  car made visible through raw sensor data.

### How to Run
```bash

git clone https://github.com/jamali-dev/f1-aiml-series.git
cd f1-aiml-series
pip install fastf1 pandas matplotlib seaborn plotly jupyter kaleido
jupyter notebook
```
Open `f1_aiml_part2_pit_wall.ipynb` and run all cells.
First run takes 2-3 minutes to download session data. 
Subsequent runs are instant from cache.

### Tools Used
- FastF1 — F1 telemetry and timing data
- Pandas — data manipulation
- Matplotlib & Seaborn — static visualisations
- Plotly — interactive charts

---

## Part 3 — Predicting the Race Winner 🏆

### What I Built
A Random Forest binary classifier trained on the complete 2025 F1 season 
(24 races, 26,689 laps) to predict race winners based on lap time delta, 
tyre age, stint number, compound and lap number.

### Key Decisions
- **2026 data excluded** — at time of building (May 2026), only 3 races were 
  available due to Bahrain and Saudi Arabia cancellations caused by regional 
  conflict, and FastF1 data restrictions. 3 races was insufficient for a 
  reliable model. Future iterations will incorporate full 2026 and 2027 seasons 
  as data becomes available.
- **Pure 2025 season used** — 24 races provides consistent regulation-era data 
  without cross-season contamination.
- **Binary classification** — predicting winner vs non-winner rather than exact 
  position. More reliable with limited data; exact position prediction noted as 
  future improvement.
- **Position feature excluded** — including current race position caused 100% 
  accuracy (overfitting). The model was reading the answer from the question.
- **Prediction threshold tuned to 0.3** — improved Winner Recall from 7% to 66%, 
  prioritising catching real winners over avoiding false alarms.

### Model Performance
| Metric | Score |
|---|---|
| Overall Accuracy | 83% |
| Winner Recall | 66% |
| Winner Precision | 19% |

Low precision is acceptable — for race prediction, missing a real winner 
is worse than occasionally predicting a false one.

### Monaco GP 2026 Prediction
The model predicted Verstappen and Norris as favourites — reflecting 
their 2025 dominance in the training data. Antonelli, who leads the 
2026 championship with 4 wins, ranked last due to limited 2025 data.

This exposes a key limitation: **the model reflects the past, not the 
present**. A driver dominating in 2026 under new regulations won't be 
recognised by a model trained entirely on 2025 patterns. This is called 
training data bias and is a known challenge in sports ML prediction.

### Limitations & Future Work
- Retrain with full 2026 and 2027 seasons as data becomes available
- Extend to full position prediction (P1-P20) with larger dataset
- Add qualifying position as a feature — especially important for Monaco
- Incorporate weather data for wet race prediction
- Normalise features to handle cross-regulation comparison

### How to Run
Open `f1_aiml_part3_winner_prediction.ipynb` and run all cells.
Requires 2025 season cache — first run takes 20-30 minutes to download.

---

## What's Coming
- **Part 4** — AI Race Engineer chatbot using GenAI & F1 MCP

---

*Built by Murtaza Jamali | May 2026*
*Data source: Official F1 timing data via FastF1 API*