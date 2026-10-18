# 🏠 Zillow Home Value Index (ZHVI) — U.S. Real Estate Analytics

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Analytics-0052CC?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power%20Query-ETL%20(M)-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Data Quality](https://img.shields.io/badge/Data%20Quality-100%25%20Valid-16a34a?style=for-the-badge)
![Status](https://img.shields.io/badge/Project%20Status-Completed-0284c7?style=for-the-badge)

> **Determining an attractive and profitable pricing approach.**  
> An end-to-end Business Intelligence solution in **Microsoft Power BI** analyzing U.S. Metropolitan Statistical Areas (MSAs) residential real estate values from **January 2000 through August 2026** (with dynamic horizon filtering such as `2020–2026`).

---

## 📑 Table of Contents
1. [Project Overview & Objective](#-1-project-overview--objective)
2. [Project Team & Governance](#-2-project-team--governance)
3. [Business Questions & Key Insights](#-3-business-questions--key-insights)
4. [Implemented KPI Dictionary](#-4-implemented-kpi-dictionary)
5. [Dataset & Power Query ETL Pipeline](#-5-dataset--power-query-etl-pipeline)
6. [Data Model Architecture (Star Schema)](#-6-data-model-architecture-star-schema)
7. [DAX Measures Reference Library](#-7-dax-measures-reference-library)
8. [Interactive Dashboard Modules](#-8-interactive-dashboard-modules)
9. [Repository Structure](#-9-repository-structure)
10. [How to Run & Update CSV Data Source](#-10-how-to-run--update-csv-data-source)

---

## 🎯 1. Project Overview & Objective

Real estate investors and market analysts need reliable historical benchmarks to distinguish between short-term price spikes and sustainable, long-term compounding growth. This project transforms raw, wide-format **Zillow Home Value Index (ZHVI)** CSV files into an interactive analytical platform.

### Key Capabilities:
* **Dynamic Horizon Benchmarking:** Allows users to select any baseline year (`Start Year Selector`) to dynamically recalculate cumulative returns, period averages, and Compound Annual Growth Rates (`CAGR %`).
* **Market Screening & Value Discovery:** Combines entry cost (`Latest Home Value`) with historical growth (`Cumulative Growth %`) to identify high-performing metropolitan areas at reasonable price points.
* **Spatial & Regional Intelligence:** Evaluates unweighted state-level appreciation across the United States to uncover geographic investment clusters.

> **⚠️ Methodological Note:** Historical home value appreciation does not automatically guarantee net investment profit. The ZHVI dataset measures estimated residential property values and does not include property taxes, maintenance costs, financing expenses, or rental yields. This dashboard is designed as a **market screening and discovery tool** to identify regions worthy of deeper due diligence.

---

## 👥 2. Project Team & Governance

| Phase | Team Member | Role & Domain | Key Responsibilities & Deliverables |
| :--- | :--- | :--- | :--- |
| **Part 1** | **Amira Mohamed Gomaa Ali** | Business Analysis & Dashboard Design | • Analyzed dataset semantics and column structures.<br>• Defined Business Questions, KPIs, and mathematical formulas.<br>• Designed dashboard wireframes and visual mapping.<br>📦 **Deliverables:** *KPI Dictionary, Business Questions, Wireframe.* |
| **Part 2** | **Aya Mostafa Ahmed AbuBakr** | Data Cleaning & Power Query ETL | • Audited raw CSV data quality, missing values, and duplicates.<br>• Filtered target MSA records and removed national aggregate rows.<br>• Executed `Unpivot` operations converting Wide to Long format.<br>📦 **Deliverables:** *Clean Dataset, Power Query Steps, Quality Notes.* |
| **Part 3** | **Mariam Ahmed Abdelmuttalib** | Data Modeling & DAX Analytics | • Designed the Star-Schema Data Model and `1:*` relationships.<br>• Built the Calendar `Date` dimension and `Start Year Selector`.<br>• Authored and validated all 10 analytical DAX measures.<br>📦 **Deliverables:** *Data Model, DAX Measures, Validation Results.* |
| **Part 4** | **Alaa Mohamed Mahmoud Genidy** | Dashboard UI/UX Development | • Implemented the approved wireframe design inside Power BI.<br>• Built the 4 interactive dashboard pages and distributed KPI cards & charts.<br>• Configured interactive slicers, cross-filtering, and navigation buttons.<br>• Unified corporate Zillow color themes and typography.<br>📦 **Deliverables:** *Interactive Power BI Dashboard Pages.* |
| **Part 5** | **Ahmed Shabaan Abdelhamed** | QA, Publishing & Documentation | • Audited and tested all KPIs, DAX measures, and slicer interactions.<br>• Cross-validated figures and visual design across all modules.<br>• Prepared project documentation, GitHub `README`, and 20-page PDF manual.<br>📦 **Deliverables:** *Tested PBIX Build, Technical Documentation, Presentation.* |

---

## 💡 3. Business Questions & Key Insights

*(Baseline Reference Horizon: Start Year = `2000` through `2026` | Scope = `All States & Metros`)*

| # | Core Business Question | Answering Dashboard & Visual | Key Analytical Finding |
| :-: | :--- | :--- | :--- |
| **1** | **What is the average home value and overall growth across markets during the period?** | *Overview* & *Investment Insights* KPI Cards + Area Trend Chart | • Multi-Year Average Home Value: **`$192.79K`**<br>• Latest Home Value: **`$300K`**<br>• Total Cumulative Growth: **`169.82%`**<br>• Compound Annual Growth Rate (CAGR): **`3.80%`** |
| **2** | **Which markets achieved the highest and lowest growth over the selected horizon?** | *Overview* Top/Lowest KPI Cards & Top 10 / Bottom 10 Bar Charts | • **Highest Growth Metro:** `Kapaa, HI` (**`552%`** cumulative / **`7.31%`** CAGR), followed by `Prineville, OR` (**`414%`**) and `Steamboat Springs, CO` (**`409%`**).<br>• **Lowest Growth Metro:** `Camden, AR` (**`42%`**) and `Forrest City, AR` (**`42%`**). |
| **3** | **Which markets combine strong historical growth with relatively reasonable entry prices?** | *Investment Insights* Scatter Plot (`Growth %` vs. `Latest Home Value`) | • Most U.S. metros cluster between **`$150K–$450K`** and **`100%–350%`** growth.<br>• Markets like `Prineville, OR` and `Glenwood Springs, CO` deliver **`>400%`** growth without requiring ultra-luxury (`$1M+`) entry capital. |
| **4** | **Is market growth continuing in the most recent year, or is momentum slowing down?** | *Overview* & *Investment Insights* `YoY Growth %` KPI Card | • Trailing 12-month growth is **`+2.26% YoY`**, confirming positive price appreciation continues, though moderating compared to the **`3.80%`** historical CAGR. |
| **5** | **How do states compare geographically, and how does any selected market differ from the benchmark?** | *Geographic Analysis* Choropleth Map, State Bar Chart & Slicers | • **Hawaii (`HI`)** ranks #1 nationwide (`>400%` average regional growth), followed by **New Hampshire**, **Maine**, **Rhode Island**, and **California**. |

---

## 📊 4. Implemented KPI Dictionary

The project's metrics are organized into three core investment pillars: **Historical Return**, **Entry Cost**, and **Market Momentum & Value Discovery**.

| KPI Name | Category | Definition & Calculation Method | Strategic Value for Investors |
| :--- | :--- | :--- | :--- |
| **Cumulative Growth %** | `Historical Return` | Percentage change between `Home Value (Start)` and `Latest Home Value`. | Measures total capital appreciation across the entire holding period. |
| **CAGR %** | `Historical Return & Stability` | Compound Annual Growth Rate using exact day-count fraction (`365.2425` days/year). | Normalizes annual growth speed and ranks the **Top 5 Most Stable Regions**. |
| **Latest Home Value** | `Entry Cost` | Average home value at the latest recorded timestamp in the dataset (`$300K`). | Estimates current capital required to enter a specific regional market. |
| **Home Value (Average)** | `Entry Cost` | Mean property value across all months from the selected Start Year to the latest date (`$192.79K`). | Provides a historical price baseline to compare against current valuation. |
| **YoY Growth %** | `Recent Momentum` | Percentage change over the most recent 12 months (`EDATE(CurrentDate, -12)`). | Tracks short-term market momentum and recent annual appreciation speed. |
| **Highest / Lowest Growth Region** | `Market Extremes` | Dynamic text identification of the #1 top-performing and #1 slowest-performing metro. | Instantly highlights market outliers (`Kapaa, HI` vs. `Camden, AR`). |
| **State Average Growth %** | `Spatial Benchmark` | Unweighted average of regional cumulative growth across all metros within each state (`AVERAGEX`). | Prevents large expensive cities from skewing state-level geographic comparisons. |

---

## 🛠️ 5. Dataset & Power Query ETL Pipeline

### Raw Data Challenges (`Metro_zhvi_uc_sfrcondo_tier_0.33_0.67_sm_sa_month.csv`)
1. **Horizontal Date Sprawl (Wide Format):** Hundreds of monthly date columns extended horizontally across the sheet (`Columns F to W+`), preventing time-series modeling.
2. **Header & Formatting Issues:** Date headers appeared as `########` in Excel and lacked proper data types.
3. **National Aggregate Row Contamination:** Row 2 contained an aggregate record for `United States` (`RegionType = country`) with an empty `StateName`, which would distort regional averages if left unfiltered.

### 8-Step Power Query Transformation (`M Language`)
1. **`Source`**: Imported raw CSV file via `Csv.Document(File.Contents(...))`.
2. **`Change Type`**: Initial text parsing of imported fields.
3. **`Promoted Headers`**: Elevated the first row to column headers (`Table.PromoteHeaders`).
4. **`Changed Type`**: Assigned `Whole Number` (`123`) to `RegionID` & `SizeRank`, and `Text` (`ABC`) to `RegionName`, `RegionType`, and `StateName`.
5. **`Unpivoted Other Columns`**: Selected the 5 fixed geographical columns and unpivoted all monthly date columns into two vertical columns (`Attribute` and `Value`).
6. **`Renamed Columns`**: Renamed `Attribute` to **`Date`** and `Value` to **`HomeValue`**.
7. **`Changed Type1`**: Cast `Date` to type **Date** and `HomeValue` to **Decimal Number (`1.2`)**.
8. **`Filtered Rows`**: Executed `Table.SelectRows(#"Changed Type1", each ([StateName] <> ""))` to remove blank-state rows and purge the `United States` aggregate record.

✅ **Post-ETL Data Quality:** `Valid: 100%` | `Error: 0%` | `Empty: 0%` across all 7 columns (`RegionID`, `SizeRank`, `RegionName`, `RegionType`, `StateName`, `Date`, `HomeValue`).

---

## 🗂️ 6. Data Model Architecture (Star Schema)

The model follows best-practice **Star Schema** design principles in Power BI:

```text
                  +------------------------+
                  |          Date          | (Calendar Dimension)
                  |------------------------|
                  | PK: Date               |
                  |     Year               |
                  |     Month Name         |
                  |     Month Number       |
                  |     Year-Month         |
                  |     YearMonth Sort     |
                  +-----------+------------+
                              |
                              | 1 (One-to-Many Active Relationship)
                              | *
                  +-----------+------------+
                  |          ZHVI          | (Fact Table)
                  |------------------------|
                  | FK: Date               |
                  |     HomeValue          |
                  |     RegionID           |
                  |     RegionName         |
                  |     RegionType         |
                  |     SizeRank           |
                  |     StateName          |
                  |     State Full Name    |
                  +------------------------+

   +-------------------------+    +-------------------------+
   |   Start Year Selector   |    |      Dax Measures       |
   |-------------------------|    |-------------------------|
   | Year (Disconnected)     |    | 10 Analytical Measures  |
   +-------------------------+    +-------------------------+
```

* **`ZHVI` (Fact Table):** Stores cleaned monthly property valuations per metro area.
* **`Date` (Calendar Dimension):** Continuous date table linked `1:*` to `ZHVI[Date]` to support DAX Time Intelligence.
* **`Start Year Selector` (Disconnected Parameter Table):** Feeds the `Start Year` slicer and passes the user's selected year into DAX variables via `SELECTEDVALUE`.
* **`Dax Measures` (Measure Container):** Dedicated table created via *Enter Data* to organize all 10 DAX measures cleanly.

---

## 🧮 7. DAX Measures Reference Library

All measures are authored using modular **Variable-Driven DAX (`VAR ... RETURN`)** and **Measure Branching**:

### 1. `Home Value`
```dax
Home Value = 
AVERAGE('ZHVI'[HomeValue])
```

### 2. `Home Value (Start)`
```dax
Home Value (Start) = 
VAR StartYear =
    SELECTEDVALUE('Start Year Selector'[Year])
VAR StartDate =
    DATE(StartYear, 1, 31)
RETURN
    CALCULATE(
        [Home Value],
        REMOVEFILTERS('Date'),
        ZHVI[Date] = StartDate
    )
```

### 3. `Latest Home Value`
```dax
Latest Home Value = 
VAR LatestDate = 
    CALCULATE(
        MAX('ZHVI'[Date]),
        REMOVEFILTERS('Date')
    )
RETURN
    CALCULATE(
        [Home Value],
        REMOVEFILTERS('Date'),
        'Date'[Date] = LatestDate
    )
```

### 4. `Home Value (Average)`
```dax
Home Value (Average) = 
VAR StartYear =
    SELECTEDVALUE('Start Year Selector'[Year])
VAR EndDate =
    CALCULATE(
        MAX(ZHVI[Date]),
        REMOVEFILTERS('Date')
    )
RETURN
    CALCULATE(
        [Home Value],
        REMOVEFILTERS('Date'),
        ZHVI[Date] >= DATE(StartYear, 1, 31),
        ZHVI[Date] <= EndDate
    )
```

### 5. `Cumulative Growth %`
```dax
Cumulative Growth % = 
VAR StartValue =
    [Home Value (Start)]
VAR EndValue =
    [Latest Home Value]
RETURN
    IF(
        StartValue > 0 && EndValue > 0,
        DIVIDE(
            EndValue - StartValue,
            StartValue
        )
    )
```

### 6. `CAGR %`
```dax
CAGR % = 
VAR StartYear =
    SELECTEDVALUE('Start Year Selector'[Year])
VAR StartValue =
    [Home Value (Start)]
VAR EndValue =
    [Latest Home Value]
VAR EndDate =
    CALCULATE(
        MAX(ZHVI[Date]),
        REMOVEFILTERS('Date')
    )
VAR Years =
    DIVIDE(
        DATEDIFF(
            DATE(StartYear, 1, 31),
            EndDate,
            DAY
        ),
        365.2425
    )
RETURN
    IF(
        StartValue > 0
            && EndValue > 0
            && Years > 0,
        POWER(
            DIVIDE(EndValue, StartValue),
            DIVIDE(1, Years)
        ) - 1
    )
```

### 7. `YoY Growth %`
```dax
YoY Growth % = 
VAR CurrentDate =
    MAX('Date'[Date])
VAR CurrentValue =
    CALCULATE(
        AVERAGE(ZHVI[HomeValue]),
        REMOVEFILTERS('Date'),
        ZHVI[Date] = CurrentDate
    )
VAR PreviousYearValue =
    CALCULATE(
        AVERAGE(ZHVI[HomeValue]),
        REMOVEFILTERS('Date'),
        ZHVI[Date] = EDATE(CurrentDate, -12)
    )
RETURN
    IF(
        NOT ISBLANK(CurrentValue)
            && PreviousYearValue > 0,
        DIVIDE(
            CurrentValue - PreviousYearValue,
            PreviousYearValue
        )
    )
```

### 8. `Highest Growth Region`
```dax
Highest Growth Region = 
VAR RegionTable =
    CALCULATETABLE(
        ADDCOLUMNS(
            ALL(ZHVI[RegionName]),
            "@Growth",
                CALCULATE(
                    [Cumulative Growth %],
                    REMOVEFILTERS(ZHVI[StateName])
                )
        ),
        REMOVEFILTERS(ZHVI[StateName]),
        REMOVEFILTERS(ZHVI[RegionName])
    )
VAR TopRegion =
    TOPN(
        1,
        FILTER(
            RegionTable,
            NOT ISBLANK([@Growth])
        ),
        [@Growth], DESC,
        ZHVI[RegionName], ASC
    )
RETURN
    CONCATENATEX(
        TopRegion,
        ZHVI[RegionName],
        ", "
    )
```

### 9. `Lowest Growth Region`
```dax
Lowest Growth Region = 
VAR RegionTable =
    CALCULATETABLE(
        ADDCOLUMNS(
            ALL(ZHVI[RegionName]),
            "@Growth",
                CALCULATE(
                    [Cumulative Growth %],
                    REMOVEFILTERS(ZHVI[StateName])
                )
        ),
        REMOVEFILTERS(ZHVI[StateName]),
        REMOVEFILTERS(ZHVI[RegionName])
    )
VAR BottomRegion =
    TOPN(
        1,
        FILTER(
            RegionTable,
            NOT ISBLANK([@Growth])
        ),
        [@Growth], ASC,
        ZHVI[RegionName], ASC
    )
RETURN
    CONCATENATEX(
        BottomRegion,
        ZHVI[RegionName],
        ", "
    )
```

### 10. `State Average Growth %`
```dax
State Average Growth % = 
AVERAGEX(
    VALUES('ZHVI'[RegionID]),
    [Cumulative Growth %]
)
```

---

## 🖥️ 8. Interactive Dashboard Modules

1. **Page 1 — `Home` (Landing Portal):**
   * Features Zillow branding, project title, strategic mission statement, and interactive navigation buttons (`Overview`, `Investment Insights`, `Geographic Analysis`).
2. **Page 2 — `Overview` (Executive Market Summary):**
   * Top filter bar (`Start Year`, `State`, `Region`), 5 KPI summary cards (`192.79K`, `169.82%`, `2.26%`, `Kapaa, HI`, `Camden, AR`), historical `AVG Home Value Trend` area chart, and `TOP 10 High-Growth` vs. `Bottom 10 Low-Growth` horizontal bar charts.
3. **Page 3 — `Investment Insights` (Compounding & Value Discovery):**
   * `CAGR %` (`3.80%`) and `Latest Home Value` (`300K`) KPI cards, `Latest Home Value and Cumulative Growth % by RegionName` scatter plot matrix, and the `TOP 5 Most Stable Region` table ranked by `CAGR %`.
4. **Page 4 — `Geographic Analysis` (Spatial Performance):**
   * `State Average Growth % by State` ranked bar chart, U.S. Choropleth heatmap (`Average Growth % by State`), and dynamic `Home Value and First State by Year` line chart.

---

## 📂 9. Repository Structure

```text
📦 Zillow-ZHVI-PowerBI-Project
 ┣ 📂 Data
 ┃ ┗ 📜 Metro_zhvi_uc_sfrcondo_tier_0.33_0.67_sm_sa_month.csv   # Raw ZHVI CSV dataset
 ┣ 📂 Dashboard
 ┃ ┣ 📊 mini projcet631.pbix                                    # Main Power BI Desktop executable
 ┃ ┣ 📂 Report                                                  # Visual layouts & theme definitions
 ┃ ┣ 📄 DataModel                                               # Compressed VertiPaq engine model
 ┃ ┣ 📄 DiagramLayout                                           # Model view diagram coordinates
 ┃ ┗ 📄 Metadata / Settings / Version                           # Internal PBIX package descriptors
 ┣ 📂 Documentation
 ┃ ┗ 📕 README_ZHVI_Project_20Pages.pdf                         # 20-Page Technical Documentation PDF
 ┗ 📜 README_Zillow_Home_Value_Index_ZHVI_Project.md            # GitHub Repository Documentation
```

---

## 🚀 10. How to Run & Update CSV Data Source

When cloning or downloading this repository to a new machine, Power BI will look for the CSV file at its original author path. Follow these steps to relink the local CSV file **without losing any of the 8 Power Query steps or 10 DAX measures**:

1. Open **`mini projcet631.pbix`** in **Microsoft Power BI Desktop**.
2. On the **Home** ribbon, click **Transform data** to open the **Power Query Editor**.
3. In the left **Queries** pane, select the **`ZHVI`** table.
4. On the **Home** ribbon, click **Advanced editor** (or click the ⚙️ gear icon next to the **`Source`** step under **Applied Steps** on the right).
5. Replace the file path inside `File.Contents("...")` with the local path where you saved `Metro_zhvi_uc_sfrcondo_tier_0.33_0.67_sm_sa_month.csv` on your computer.
6. Click **Done** (or **OK**), then click **Close & Apply** in the top-left corner.
7. All visuals, relationships, and DAX measures will refresh automatically.