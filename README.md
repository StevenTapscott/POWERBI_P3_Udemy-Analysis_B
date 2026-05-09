#  Building a BI App – Udemy Course Performance Analysis

##  Overview  
This project focuses on building an end-to-end Business Intelligence application in Power BI using the Udemy Online Education Courses dataset. The objective was to analyse course engagement and performance metrics to identify which courses may require improvement and why.

The project involved data preparation, data modelling, DAX measure creation, dashboard development, and publishing the final report to Power BI Service.

---

##  Objectives  
- Analyse course engagement using subscriber and review metrics  
- Identify underperforming courses requiring improvement  
- Build an interactive Power BI dashboard for stakeholder analysis  
- Create KPI-driven insights using DAX measures  
- Publish the report to Power BI Service  

---

##  Tools & Technologies  
- Power BI  
- Power Query  
- DAX (Data Analysis Expressions)  
- Power BI Service  
- Data Modelling  
- Data Visualisation  

---

##  Dataset  
**Udemy Online Education Courses Dataset**

Dataset includes:
- Course ID  
- Course Title  
- URL  
- Paid  
- Price ($)  
- No. of subscribers  
- No. of reviews  
- No. of lectures  
- Level  
- Content Duration (Hours)  
- Published Timestamp  
- Subject  

---

##  Key Steps  

### 1. Data Preparation  
- Imported dataset into Power BI  
- Cleaned and transformed data using Power Query  
- Verified data types and formatting  
- Structured data for analysis and reporting  

### 2. Data Modelling  
Created calculated columns for enhanced business analysis and segmentation:

```DAX
Price Category =
SWITCH(
    TRUE(),
    Courses[Price ($)] = 0, "Free",
    Courses[Price ($)] <= 50, "Low Cost",
    Courses[Price ($)] <= 100, "Mid Range",
    "Premium"
)
```

```DAX
Duration Category =
SWITCH(
    TRUE(),
    Courses[Content Duration (Hours)] < 2, "Short",
    Courses[Content Duration (Hours)] < 10, "Medium",
    "Long"
)
```

```DAX
Popularity Category =
SWITCH(
    TRUE(),
    Courses[No. of subscribers] < 1000, "Low",
    Courses[No. of subscribers] < 10000, "Moderate",
    "High"
)
```

```DAX
Engagement Risk =
SWITCH(
    TRUE(),
    Courses[No. of subscribers] > 10000 &&
    Courses[No. of reviews] < 100,
    "High Risk",

    Courses[No. of reviews] > 500,
    "Healthy",

    "Moderate"
)
```

```DAX
Estimated Revenue =
Courses[Price ($)] * Courses[No. of subscribers]
```

---

### 3. DAX Measure Creation  

Key KPI measures included:

```DAX
Total Courses = DISTINCTCOUNT(Courses[Course ID])
```

```DAX
Total Subscribers = SUM(Courses[No. of subscribers])
```

```DAX
Total Reviews = SUM(Courses[No. of reviews])
```

```DAX
Average Price = AVERAGE(Courses[Price ($)])
```

```DAX
Average Duration = AVERAGE(Courses[Content Duration (Hours)])
```

```DAX
Review Rate =
DIVIDE(
    [Total Reviews],
    [Total Subscribers]
)
```

```DAX
Avg Subscribers per Course =
DIVIDE(
    [Total Subscribers],
    [Total Courses]
)
```

```DAX
Total Revenue = SUM(Courses[Estimated Revenue])
```

---

##  Dashboard Features  

### KPI Cards  
- Total Courses  
- Total Subscribers  
- Estimated Revenue Potential  
- Review Rate  

### Visualisations  
- Subscriber analysis by subject  
- Review rate analysis by duration category  
- Scatter plot for course engagement analysis  
- Course publishing trends over time  

### Interactive Features  
- Subject slicers  
- Level filters  
- Price category filters  
- Duration category filters  
- Popularity segmentation  

---

##  Key Insights  
- Web Development courses generated the highest subscriber engagement across the platform  
- Longer-duration courses achieved stronger review rates than shorter courses  
- Several highly subscribed courses demonstrated relatively low engagement metrics  
- Beginner-level courses showed stronger participation trends compared to advanced-level content  

---

##  Business Value  
- Demonstrates end-to-end BI workflow development using Power BI  
- Supports data-driven decision-making for course improvement prioritisation  
- Highlights the importance of engagement analysis within online learning platforms  
- Showcases practical dashboard design, KPI reporting, and analytical storytelling skills  

---

##  Challenges Faced  
- Designing meaningful calculated categories for analysis  
- Building effective DAX measures for KPI reporting  
- Managing scatter plot aggregation and visual clarity  
- Balancing dashboard readability with analytical depth  

---

##  Outcome  
Successfully developed and published an interactive Power BI report analysing course engagement patterns using subscribers, reviews, duration, and pricing metrics. The project demonstrates practical skills in Power BI, DAX, data modelling, and business intelligence reporting.

---

##  Dashboard Preview  
Screenshots will be in the 'screenshots' folder.
---

##  Report Access  
Published to Power BI Service via My Workspace. Link is found here - (https://app.powerbi.com/groups/me/reports/b1b8bee7-26f6-40a2-9a1e-cf5c27b25df6/3e650dcd31584a7e7060?experience=power-bi)
---

##  Future Improvements  
- Implement Row-Level Security (RLS)  
- Expand KPI analysis with additional learner engagement metrics  
- Create advanced time intelligence measures  
- Enhance dashboard interactivity and drill-through functionality  
