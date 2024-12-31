# Project 1: SQL Analysis of Startup Trends

 Description
This project focuses on analyzing startup trends using SQL queries. The dataset, `TrendsInStartups_Explorin`, includes information on startups, such as their names, valuations, funding stages, locations, and sizes. The analysis involves extracting valuable insights through various SQL queries.

---
 Objectives

1. **Calculate the total number of companies in the dataset**  
   **Query:**  
   ```sql
   SELECT count(name) FROM TrendsInStartups_Explorin;
   ```

2. **Determine the total value of all companies in the dataset**  
   **Query:**  
   ```sql
   SELECT sum(valuation) FROM TrendsInStartups_Explorin;
   ```

3. **Find the highest amount raised by a startup at the 'Seed' stage**  
   **Query:**  
   ```sql
   SELECT MAX(amount_raised) FROM TrendsInStartups_Explorin WHERE stage = 'Seed';
   ```

4. **Identify the year when the oldest company on the list was founded**  
   **Query:**  
   ```sql
   SELECT MIN(founded_year) FROM TrendsInStartups_Explorin;
   ```

5. **Calculate the average valuation within each startup category**  
   **Query:**  
   ```sql
   SELECT DISTINCT(sector), AVG(valuation) FROM TrendsInStartups_Explorin GROUP BY sector;
   ```

6. **Determine the top locations with the highest number of startups**  
   **Query:**  
   ```sql
   SELECT DISTINCT(location), MAX(size) FROM TrendsInStartups_Explorin GROUP BY location;
   ```

7. **Calculate the average size of startups in each location where the average size exceeds 500**  
   **Query:**  
   ```sql
   SELECT DISTINCT(location), AVG(size) FROM TrendsInStartups_Explorin GROUP BY location HAVING AVG(size) > 500;
   ```

8. **Find the top 5% of startups with the highest valuations**  
   **Query:**  
   ```sql
   SELECT DISTINCT(name), SUM(valuation) AS Valued FROM TrendsInStartups_Explorin GROUP BY name ORDER BY Valued DESC LIMIT 15;
   ```

9. **Identify startups that have raised funding in every stage (Seed, Series A, Series B, etc.)**  
   **Query:**  
   ```sql
   SELECT name, COUNT(stage) AS A FROM TrendsInStartups_Explorin GROUP BY name HAVING A = 4;
   ```

10. **Calculate the percentage growth in valuation from Seed stage to Series A for each startup**  
    **Query:**  
    ```sql
    SELECT
        s.name AS StartupName,
        s.valuation AS SeedValuation,
        a.valuation AS SeriesAValuation,
        ((a.valuation - s.valuation) * 100 / s.valuation) AS PercentageGrowth
    FROM
        (SELECT name, valuation FROM TrendsInStartups_Explorin WHERE stage = 'Seed') s
    JOIN
        (SELECT name, valuation FROM TrendsInStartups_Explorin WHERE stage = 'Series A') a
    ON s.name = a.name;
    ```

---

## Dataset
**Name:** `TrendsInStartups_Explorin`  
**Attributes:**
- `name`: Name of the startup
- `valuation`: Valuation of the startup
- `amount_raised`: Amount raised by the startup
- `stage`: Funding stage (e.g., Seed, Series A, Series B)
- `founded_year`: Year the startup was founded
- `sector`: Sector or category of the startup
- `location`: Location of the startup
- `size`: Size of the startup (e.g., number of employees or other metric)

---

## Author
**Name:** Adya Verma  
**Class:** MBA 1st Year

---


---

## Contributions
Contributions and suggestions to improve the project or add new queries are welcome. Please submit a pull request or open an issue on this repository.

