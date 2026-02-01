# MSCS_634_Lab_1: Data Visualization, Data Preprocessing, and Statistical Analysis Using Python in Jupyter Notebook for MSCS 634

**Name:** Avijit Saha  
**Course:** MSCS 634 – Data Mining / Data Analytics  
**Lab:** Lab 1  

---

## Purpose of the Lab
The purpose of this lab is to demonstrate practical skills in data exploration, data visualization, data preprocessing, and statistical analysis using Python and Jupyter Notebook. The lab focuses on transforming raw, real-world data into a clean and structured format that can be analyzed to extract meaningful insights. Through visualization and statistical techniques, the dataset is examined to identify trends, relationships, outliers, and overall data characteristics.

This lab also reinforces the use of professional data science tools such as Pandas, Matplotlib, Seaborn, and Scikit-learn, as well as proper documentation and version control through GitHub.

---

## Dataset Description
The dataset used in this lab is the **Global Superstore Sales Dataset**, which contains transactional, customer, and shipping information for retail orders. The dataset includes both numerical and categorical features, as well as time-based attributes, making it well-suited for visualization, preprocessing, and statistical analysis.
**Data Source**: https://www.kaggle.com/datasets/fatihilhan/global-superstore-dataset

### Key Attributes
- **Category / Sub.Category** – Product classification  
- **Sales** – Total sales amount for each order  
- **Profit** – Profit generated from each order  
- **Quantity** – Number of units ordered  
- **Discount** – Discount applied to the order  
- **Shipping.Cost** – Cost associated with shipping the order  
- **Segment** – Customer segment (Consumer, Corporate, Home Office)  
- **Region / Market / Country / State / City** – Geographic information  
- **Order.Date / Ship.Date / Year / weeknum** – Time-based attributes  
- **Record_Count** – Indicator column representing transaction count  

---

## Tools and Technologies Used
- **Python 3.12**  
- **Jupyter Notebook**  
- **Pandas** – Data loading, cleaning, and manipulation  
- **Matplotlib & Seaborn** – Data visualization  
- **Scikit-learn** – Data scaling and normalization  
- **GitHub** – Version control and lab submission  

---

## Data Visualization Summary
Several visualization techniques were applied to explore patterns, distributions, and relationships in the dataset:

### Scatter Plot (Sales vs Profit)
This plot revealed a generally positive relationship between sales and profit. However, some high-sales transactions resulted in negative profit, indicating the impact of discounts and shipping costs on overall profitability.

### Bar Chart (Total Sales by Category)
The bar chart showed that certain product categories contribute significantly more to overall revenue, helping identify the strongest and weakest sales segments.

### Box Plot (Profit Distribution)
The box plot highlighted the spread of profit values and identified potential outliers that were examined during preprocessing.


---

## Data Preprocessing Summary

### Column Standardization
A non-English column name (`记录数`) was renamed to `Record_Count` to improve readability, prevent font rendering issues in visualizations, and ensure consistent processing during statistical and correlation analysis.

### Missing Values
The dataset was evaluated using `df.isnull().sum()`, and no missing values were detected. Therefore, no imputation or row/column removal was required.

### Outlier Detection and Removal
Outliers in the **Sales** column were identified using the Interquartile Range (IQR) method. Values outside the lower and upper bounds were removed to prevent skewing of statistical results and visualizations.

### Data Reduction
- **Sampling:** A random 50% sample of the cleaned dataset was taken to reduce data size while preserving diversity.  
- **Dimension Reduction:** Less relevant identifier columns such as `Row.ID` were removed to focus on meaningful analytical features.

### Data Scaling and Discretization
- **Min-Max Scaling:** Applied to numerical columns (Sales and Profit) to normalize values between 0 and 1.  
- **Discretization:** Sales values were grouped into three categories: Low, Medium, and High, enabling easier interpretation and categorical analysis.

---

## Statistical Analysis Summary

### Central Tendency Measures
The following measures were calculated for numerical attributes:
- Minimum  
- Maximum  
- Mean  
- Median  
- Mode  

These measures provided insight into typical transaction values and overall dataset behavior.

### Dispersion Measures
The dataset’s variability was analyzed using:
- Range  
- Quartiles (Q1 and Q3)  
- Interquartile Range (IQR)  
- Variance  
- Standard Deviation  

These metrics helped assess the spread and consistency of sales, profit, and shipping costs.

### Correlation Analysis
A correlation matrix was computed to identify relationships between numerical variables. Key findings include:
- **Sales and Shipping.Cost** showed a strong positive correlation, indicating that higher sales are often associated with higher shipping expenses.  
- **Sales and Quantity** demonstrated a moderate positive relationship, suggesting that larger orders tend to generate higher revenue.  
- **Discount and Profit** showed a strong negative correlation, confirming that higher discounts generally reduce profitability.  

The `Record_Count` column was excluded from the correlation analysis because it showed no variance, resulting in undefined (NaN) correlation values.

---

## Challenges Faced and Decisions Made During the Lab

- One of the main challenges encountered during this lab was handling non-standard column names in the dataset. The dataset included a column labeled "记录数," which caused font-rendering warnings and reduced readability in visualizations and correlation heatmaps. To address this, a design decision was made to standardize the schema by renaming the column to Record_Count, improving compatibility with plotting libraries and ensuring consistent feature naming throughout the analysis.
Starting off, figuring out when to shrink the data proved difficult. Instead of trimming things right away, work began by fixing messy entries, looking into gaps, and then exploring trends. Only after those steps did the process begin to shrink in size. That way, each feature had a chance to show its worth before being removed. Patterns stayed clearer because choices came later, not sooner.
- Midway through processing, picking how to handle number columns became central. Though Sales and Shipping.Cost stretched much higher than Discount or Quantity, their scale needed adjusting. To evenly align values, Min-Max scaling was used to scale those wider-ranging fields. That shift helped when visually spotting patterns across variables. Meanwhile, only some ongoing measures were split into bins, making group contrasts clearer without distorting the original spread.
- Plotting took time, so speed mattered. A smaller slice of data helped - picked at random, but still looked like the full set. This sample made visuals quicker to build without changing how things really lined up. Size stayed manageable, yet patterns held true.
