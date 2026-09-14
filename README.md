# Premier League 2024/2025 Performance Tracker & Squad Analytics

An end-to-end data analytics and business intelligence project modeling individual player performance, squad age reliance, disciplinary risk, and goal dependencies across the 2024/2025 English Premier League season using Microsoft Excel (Power Query, Power Pivot, and DAX).

## Project Overview
Modern football management relies heavily on data-driven scouting, squad rotation, and squad composition strategy rather than intuition alone. Traditional scouting often overemphasizes raw goal tallies, leading to overvalued transfers and skewed performance assessments.

This interactive dashboard acts as a decision-support instrument for club managers, performance analysts, and talent scouts to:
* Differentiate pure open-play productivity from dead-ball/penalty reliance.
* Evaluate squad age distribution and mitigate future squad aging crises.
* Monitor tactical disciplinary risk via per-90-minute card metrics.
* Map foreign vs. domestic player distributions to satisfy league homegrown quotas.

## Data Architecture & Star Schema
The raw dataset (574 records sourced from Kaggle) was transformed and normalized from a flat table into a structured Star Schema using Excel Power Query to support granular slice-and-dice operations:

* **Fact Table:**
  * `Fact_PlayerStats`: Contains granular match performance metrics (Minutes played, starts, 90s, G, A, G-PK, PK, PKatt, Yellow/Red cards, and per-90 normalized figures).
* **Dimension Tables:**
  * `Dim_Player`: Stores `Player_ID`, player names, age, birth year, nationality, and calculated `Age_Group` bands (`U-21`, `22–28`, `>28`).
  * `Dim_Squad`: Stores `Squad_ID` and team names.
  * `Dim_Position`: Stores `Pos_ID` and playing role designations.

### Data Cleaning & Preprocessing Highlights
* **Text Extraction:** Cleaned nation fields using custom split delimiters to isolate standardized country codes.
* **Integrity Handling:** Handled missing rows, dropping incomplete player entries down to 573 clean observations.
* **Relationship Management:** Established 1-to-Many (`1:*`) relationships in Power Pivot connecting dimensions to the central fact table.

## Key Business Findings & Tactical Insights
* Penalty Dependency vs. Open-Play Efficiency: Mohamed Salah led the league with 47 direct goal contributions (29 goals, 18 assists; 20 open-play goals). Visualizing penalty contributions revealed major stylistic variances: Justin Kluivert (Bournemouth) relied on penalties for 50% of his goals (6 of 12), whereas Matheus Cunha (Wolves) recorded 100% of his 15 goals from open play.
* Workload & Squad Aging Risk: The core productive demographic (Ages 22–28) captured 64% of total league minutes (483,469 minutes). Young talents (U-21) accounted for only 13% of total playing time, signaling an urgent squad succession and regeneration bottleneck across several clubs.
* Disciplinary Anomalies: Samuel Amo-Ameyaw recorded the highest card frequency at 0.33 cards per 90 minutes (~1 card every 3 full matches), identifying tactical fouls but also highlighting sample-size skew on lower-minute fringe players.
* Talent Pipeline & Homegrown Balance: Domestic English talent represented 33.9% (194 of 573 players), followed by Brazil (34 players), France (25), and Portugal (23), providing benchmark data for league homegrown roster compliance.

## Strategic Recommendations
* Scouting Strategy: Incorporate Non-Penalty Goal Ratio and Open-Play Conversion metrics as non-negotiable filters to avoid purchasing overvalued penalty-inflated attackers.
* Squad Regeneration Policy: Mandate cup/low-risk match rotation quotas to elevate U-21 minutes from 13% to at least 20%, dampening injury risks among senior starters.
* Disciplinary Thresholds: Institute minimum playing-time filters before ranking per-90 metrics to eliminate low-sample statistical bias.
* Recruitment Cost Optimization: Satisfy homegrown quotas via low-cost academy pathways while reserving marquee transfer budgets for undervalued foreign talent pools.

## Tech Stack & Tools
* Platform: Microsoft Excel (Power Query, Power Pivot, Pivot Charts)
* Modeling Paradigm: Star Schema, Dimensional Modeling, Relational Integrity
* Formulas: Data Analysis Expressions (DAX)

## Contributors 
* Nacito Florisen Astari 
* Aditya Maulana
* Aditya Naufal Erlangga
* Gideon Manggaprouw
* Mohamad Arya Fadlullah
* Thio Michael Yulianto
