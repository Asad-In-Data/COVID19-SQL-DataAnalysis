# SQL-Chronicles-Unmasking-COVID-19-Through-Data
                                       When the world fell silent under an invisible threat,
                                         I picked up my keyboard—and with every SQL query, 
                                             I became both detective and storyteller
## 🧠 Overview
This project explores the impact of COVID-19 across the globe using SQL-based data analysis. From infection rates to vaccination trends, this analysis covers it all by querying a rich dataset containing detailed records of COVID cases, deaths, and vaccinations by country and date.

You’ll find a powerful story told entirely through data — combining technical depth, real-world insights, and impactful visualizations (Power BI add-ons coming soon).
## 🌐 Dataset Source
**Dataset used:**

        COVID-19 Data from **Our World in Data**
Tables:
- Covid_deaths
- Covid_vaccinations

## 🎯 Key Objectives
- Calculate global & country-wise infection and death percentages
- Analyze death rates by population
- Identify countries with highest death toll
- Visualize vaccination trends using rolling sums
- Use temporary tables and views to modularize logic
- Enable global comparison of case severity and vaccine progress

## 🧰 SQL Tools & Techniques Used
- **Joins** (Inner Join between deaths & vaccinations)
- **CTEs** (Common Table Expressions)
- **Window Functions** (OVER clause for rolling calculations)
- **Aggregation** (SUM, MAX, AVG)
- **Temporary Tables** (#TempTable)
- **Views** for reusable query logic
- **Data Cleaning & Casting** (e.g., CAST, CONVERT)
- **Percentage Calculations** for population-based insights

## 📊 CORE INSIGHTS DISCOVERED
Here are just a few of the mind-blowing discoveries this project unearthed:
### 📈 Total Cases vs Population
In countries like Pakistan, despite a lower testing ratio, infections reached noticeable population percentages.
``` sql
(total_cases / population) * 100 AS PercentPopulationInfected
```

### 💀 Deaths per Population
Some countries showed alarming death-to-population ratios, exposing fragilities in their healthcare systems.
```sql
(total_deaths / population) * 100 AS DeathPercentPopulation
## Highest Death Count
MAX(CAST(total_deaths AS INT)) AS TotalDeathCount
```
### 🌍 Global Death Percentage
The global death rate hovered at a critical percentage — signaling urgent global response coordination.
```sql
SUM(new_cases + total_cases) AS total_cases,
SUM(CAST(new_deaths AS INT)) AS total_deaths,
(SUM(CAST(new_deaths AS INT)) / SUM(new_cases)) * 100 AS DeathPercentage

```
### 💉 Rolling Vaccination Rates
By partitioning vaccination data by location and ordering by date, I analyzed how fast or slow people were being vaccinated — country by country, day by day.
```sql
SUM(CONVERT(BIGINT, vac.new_vaccinations)) OVER (
PARTITION BY dea.location ORDER BY dea.location, dea.date
) AS RollingPeopleVaccinated
```
## 🤝 Impact & Next Steps
- **For Analysts:** A template for pandemic data storytelling—plug in any global crisis dataset and let SQL narrate the tale.
- **For Decision-Makers:** A proof-of-concept for real-time dashboards that blend performance (rolling sums) with per-capita context.
- **For Me:** A step toward more advanced data-driven storytelling—next on deck: integrating Python for deeper statistical modeling and interactive web dashboards.

## 🛠️ How to Use
**0.** Download or clone this repository

**1.** Import the dataset (CSV ) into your local SQL environment (MySQL, PostgreSQL, or MS SQL Server).

**2.** Run the queries in covid_analysis.sql in order — each is documented for clarity.

**3.** Use the final views for Power BI or Tableau visualization.

## 🖼️ Screenshots

![SQL 1](https://github.com/user-attachments/assets/0cbdb5a2-1007-4574-952c-834ea04f07db)



## 👨‍💻 Author
**Asad Ali**
*Data Analyst | Robotics Enthusiast | Lifelong Learner*

📫 Connect with me on LinkedIn

📁 Visit My Portfolio 

