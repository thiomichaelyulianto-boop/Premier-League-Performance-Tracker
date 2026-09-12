# Premier League 2024/2025 Performance Tracker & Squad Analytics

An end-to-end data analytics and business intelligence project modeling individual player performance, squad age reliance, disciplinary risk, and goal dependencies across the 2024/2025 English Premier League season using **Microsoft Excel (Power Query, Power Pivot, and DAX)**.

## Project Overview
Modern football management relies heavily on data-driven scouting, squad rotation, and squad composition strategy rather than intuition alone. Traditional scouting often overemphasizes raw goal tallies, leading to overvalued transfers and skewed performance assessments.

This interactive dashboard acts as a decision-support instrument for club managers, performance analysts, and talent scouts to:
* Differentiate pure open-play productivity from dead-ball/penalty reliance.
* Evaluate squad age distribution and mitigate future squad aging crises.
* Monitor tactical disciplinary risk via per-90-minute card metrics.
* Map foreign vs. domestic player distributions to satisfy league homegrown quotas.

## Data Architecture & Star Schema
The raw dataset (574 records sourced from FBref/Kaggle) was transformed and normalized from a flat table into a structured **Star Schema** using Excel Power Query to support granular slice-and-dice operations:

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
