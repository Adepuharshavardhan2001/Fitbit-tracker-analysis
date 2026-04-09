 Fitbit User Activity & Health Analytics
 
End-to-end data science project analyzing 33 Fitbit users over 31 days to uncover activity patterns, predict calorie burn, and segment users by lifestyle.

 Problem Statement
 
Fitness trackers generate massive amounts of data, but raw numbers don't drive behavior change. How can we transform wearable data into actionable health insights?

This project answers:

What daily behaviors predict calorie burn?

Can we predict tomorrow's sleep from today's activity?

How do different user types (active vs sedentary) behave?

 Dataset
 
Aspect	Details

Source	Fitbit Fitness Tracker Data (Kaggle)

Duration	April 12, 2016 – May 12, 2016

Users	33 unique participants

Records	2.4M+ heart rate + 1.3M minute-level records

Files	18 CSV files (daily, hourly, minute granularity)

Data Types:

Daily: steps, calories, intensity minutes, sleep

Hourly: step counts, calories, intensity

Minute-level: METs, heart rate (5-second intervals), sleep stages

Tech Stack


Python 3.12          → Core language

Pandas/NumPy         → Data processing

MySQL + SQLAlchemy   → Database storage

Matplotlib/Seaborn   → Visualization

Scikit-learn         → ML models & clustering

Project Workflow

Raw CSVs (18 files)
       ->
Data Cleaning & Standardization
       ->
MySQL Database (10+ tables)
       ->
Feature Engineering (12 behavioral metrics)
       ->
EDA & Visualization
       ->
ML Models (Regression + Clustering)
       ->
Actionable Insights

Feature Engineering

Behavioral Features

Feature	Formula

Step Variability	STDDEV(daily_steps)

Sleep Regularity	STDDEV(sleep_minutes) / AVG(sleep_minutes)

Sedentary Ratio	sedentary_minutes / 1440

Circadian Features

Feature	Time Window

Morning Ratio	6 AM – 11 AM

Afternoon Ratio	12 PM – 5 PM

Evening Ratio	6 PM – 11 PM

Energy Efficiency Features

calories_per_step = calories / total_steps

calories_per_active_minute = calories / active_minutes

Key Findings

1. Average User Profile
   
Daily Steps:      8,515 steps

Calories Burned:  2,389 kcal

Sleep Duration:   422 min (≈7 hours)

Sedentary Time:   712 min (≈12 hours)

Very Active Time: 25 min/day only!

2. Circadian Pattern

Peak activity:     5:00 PM – 8:00 PM

Lowest activity:   2:00 AM – 4:00 AM

Most consistent:   Morning walkers (6-8 AM)

3. Activity vs Sleep Paradox
4. 
Activity Level	Next-Day Sleep

Low (<5k steps)	454 min

Moderate (5k-10k)	425 min

High (>10k steps)	401 min

Insight: Higher activity doesn't guarantee better sleep. Sleep quality depends on factors beyond step count.

 Machine Learning Results
 
Task 1: Calories Burned Prediction

Model	R² Score	RMSE	MAE

Linear Regression	0.40	484	385

Random Forest	0.89	240	165

Gradient Boosting	0.91	225	152

Best Model: Gradient Boosting (after hyperparameter tuning)

Top 3 Features:

Evening activity ratio (6-11 PM)

Calories per step

Sedentary minutes

Task 2: Next-Day Sleep Prediction

Model	R² Score

Linear Regression	-0.01

Random Forest	-0.11

Conclusion: Sleep is NOT predictable from activity data alone. Missing factors: stress, diet, light exposure, mental health.

User Segmentation (GMM Clustering)

Using Gaussian Mixture Model, users split into 3 distinct lifestyle clusters:

Cluster	Size	Characteristics	Avg Steps	Avg Sleep

0 - Active Regimen	21 users	High activity, consistent	8,354	397 min

1 - Sedentary	2 users	Very low activity, irregular	5,097	65 min

2 - High Sleepers	1 user	Low activity, excellent sleep	3,477	652 min

PCA Visualization:


Component 2
    ↑
    |      ●●● (Active)
    |    ●●●
    |  ●
    |            ■ (Sedentary)
    |                ▲ (High Sleepers)
    └──────────────────────────→ Component 1
Sample Visualizations

Circadian Activity Pattern

Average Steps
   600│                    ╱‾‾╲
   500│                  ╱    ╲
   400│                ╱      ╲___
   300│              ╱
   200│            ╱
   100│    _______╱
     0└────────────────────────────────→ Hour
       0   4   8   12  16  20  24
Correlation Heatmap

              Steps  Sleep  Calories  Sedentary
Steps          1.00  -0.11    0.59     -0.45
Sleep         -0.11   1.00   -0.08      0.21
Calories       0.59  -0.08    1.00     -0.62
Sedentary     -0.45   0.21   -0.62      1.00

 Business Recommendations
 
User Type	Recommendation

Active Users	Maintain evening activity (6-8 PM) for optimal calorie burn

Sedentary Users	Target 5,000 steps/day as first milestone

Poor Sleepers	Focus on consistency, not intensity

All Users	25 min of very active minutes is too low → increase to 45 min


Future Improvements

Time series forecasting (LSTM) for step prediction

Streamlit dashboard for non-technical users

Incorporate weather data to explain activity variation

Collect qualitative data (mood, stress) for sleep prediction

Author
A.Harshavardhan
Data Science Portfolio Project

adepuharshavardhan2001.com
LinkedIn
GitHub

 Key Achievements 
 Processed 2.4M+ heart rate records across 18 data sources
 Engineered 12 behavioral features (circadian, energy efficiency, variability)
 Achieved 91% R² in calorie prediction using Gradient Boosting
 Identified 3 actionable user segments via GMM clustering
 Built end-to-end pipeline: raw CSVs → MySQL → ML models → insights

