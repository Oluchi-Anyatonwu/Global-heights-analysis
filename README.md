# Global-heights-analysis

### Project Overview:
The Global Heights Analysis project aimed to provide a comprehensive understanding of height trends worldwide using a rich dataset encompassing sex, year, age group, mean height, uncertainty intervals, and standard errors. The primary goal was to uncover insights into temporal trends, sexual dimorphism, age-related patterns, and other factors influencing mean heights across different demographics

![GLOBAL HEIGHTS DASHBOARD](https://github.com/Oluchi-Anyatonwu/Global-heights-analysis/assets/61971994/264178ec-724b-4eec-a66c-02969368b9da)

### Tools Used:
The project employed a combination of SQL for data querying and analysis, and Power BI for data visualization. SQL allowed for efficient extraction and transformation of the dataset, while Power BI was instrumental in creating dynamic and interactive visualizations for effective communication of the findings.

### Expected Deliverables:
- A SQL script for data extraction and exploratory analysis.
- A Power BI dashboard providing an interactive visualization of key insights.
- Documentation detailing data cleaning, exploratory data analysis (EDA), and data analysis procedures.
- A portfolio report summarizing project overview, tools used, expected deliverables, benefits, data cleaning/preparation, exploratory data analysis, data analysis, results/findings, and recommendations.

### Benefits:
- Comprehensive understanding of global height trends.
- Clear visual representation of key patterns and variations.
- Insights into factors contributing to mean height differences.
- Interactive dashboard for ongoing exploration and analysis.

### Data Cleaning/Preparation:
The initial phase involved thorough data cleaning to address missing values, outliers, and inconsistencies. Standardizing data formats, handling duplicates, and addressing any anomalies ensured the dataset's reliability for subsequent analysis.

### Exploratory Data Analysis:
EDA involved summarizing key statistics, visualizing distributions, and identifying potential correlations. Exploring the dataset's structure and characteristics provided valuable insights, guiding subsequent analyses.

### Data Analysis:
Utilizing SQL queries, the analysis included temporal trend assessments, sexual dimorphism comparisons, age-related pattern explorations, uncertainty and standard error assessments, outlier detection, and cohort analyses. Power BI visualizations enhanced the communication of these findings.

```
USE my_database;
```

```
SELECT *
FROM `global_height`;
```

-- Temporal Trends
```
SELECT year, ROUND(AVG(`Mean height`),2) AS avg_height
FROM global_height
GROUP BY year;
```

-- Sexual Dimorphism
```
SELECT sex, ROUND(AVG(`Mean height`),2) AS avg_height
FROM global_height
GROUP BY sex;
```

-- Age Related Patterns
```
SELECT `Age group`,
ROUND(AVG(`Mean height`)) AS avg_height
FROM global_height
GROUP BY `Age group`;
```

-- Uncertainty Assessment
```
SELECT year, sex, ROUND(AVG(`Mean height`)) AS avg_height, ROUND(AVG(`Mean height lower 95% uncertainty interval`)) AS avg_uncertainty
FROM global_height
GROUP BY year,sex;
```

-- Standard Error Analysis
```
SELECT year, sex, ROUND(AVG(`Mean height`)) AS avg_height, ROUND(AVG(`Mean height standard error`),2) AS avg_standard_error
FROM global_height
GROUP BY year,sex;
```

-- Outlier Detection
```
SELECT *
FROM `global_height`
WHERE `Mean height` < (SELECT AVG(`Mean height`) - 2 * STDDEV(`Mean height`) FROM `global_height`) 
OR `Mean height` > (SELECT AVG(`Mean height`) + 2 * STDDEV(`Mean height`) FROM `global_height`); 
```

### Results/Findings:
- Temporal Trends: Clear patterns of height changes over the years.
- Sexual Dimorphism: Apparent differences in mean heights between sexes.
- Age-related Patterns: Variances in mean heights across different age groups.
- Uncertainty Assessment: Insight into the precision of mean height estimates.
- Standard Error Analysis: Evaluation of the reliability of mean height estimates.
- Outlier Detection: Identification of potential anomalies in the data.

### Recommendations:
- Further investigation into years with high uncertainty to improve data quality.
- Consider additional variables (e.g., socioeconomic factors) for a more comprehensive analysis.
- Regular updates to the dataset to capture evolving global height trends.
- Validation of findings through comparison with external studies or datasets.
