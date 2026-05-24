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

## What's Coming
- **Part 3** — Predict Race Winners using Scikit-Learn
- **Part 4** — AI Race Engineer chatbot using GenAI

---

*Data source: Official F1 timing data via FastF1 API*
