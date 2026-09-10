Retail Sales Visualization, Relationship Analysis & Business Insights

Project Overview

This project performs Exploratory Data Analysis (EDA) on a retail/superstore sales dataset.

The notebook focuses on:

Cleaning and preparing the dataset

Checking the dataset structure and data types

Checking missing values and duplicate records

Visualizing Profit and Sales distributions

Comparing profit across Category, Sub-Category, and Region

Studying the relationship between Discount and Profit

Creating a correlation heatmap for numerical attributes

Technologies Used

Python

Pandas

Matplotlib

Seaborn

Jupyter Notebook / Google Colab

Dataset

The notebook loads the dataset using:

df = pd.read_csv("/content/superstore_raw.csv")

Make sure superstore_raw.csv is available in the notebook environment before running the cells.

Steps Performed

1. Import Libraries

import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

Pandas is used for data handling, while Matplotlib and Seaborn are used for visualization.

2. Load the Dataset

df = pd.read_csv("/content/superstore_raw.csv")

The retail dataset is loaded into a Pandas DataFrame.

3. Explore the Dataset

The notebook checks:

First few rows using df.head()

Number of rows and columns using df.shape

Column names using df.columns

Data types using df.dtypes

Selected business columns such as Sales, Quantity, Discount, Profit, Category, Sub-Category, and Region

4. Data Cleaning

The categorical columns are formatted using title case:

df['Category'] = df['Category'].str.title()
df['Sub-Category'] = df['Sub-Category'].str.title()
df['Region'] = df['Region'].str.title()

Order Date and Ship Date are converted to datetime:

df['Order Date'] = pd.to_datetime(
    df['Order Date'],
    format='mixed',
    errors='coerce'
)

df['Ship Date'] = pd.to_datetime(
    df['Ship Date'],
    format='mixed',
    errors='coerce'
)

5. Data Quality Checks

The notebook checks for:

df.isnull().sum()

and duplicate rows:

df.duplicated().sum()

6. Profit Distribution

A box plot is created to visualize the distribution of profit values.



7. Sales Distribution

A box plot is used to visualize the distribution of sales values.



8. Total Profit by Category

A bar plot compares total profit across product categories.



9. Total Profit by Sub-Category

The notebook groups the data by Sub-Category and calculates total profit:

subcategory_profit = df.groupby("Sub-Category")["Profit"].sum()



10. Profit Distribution by Category

A box plot compares profit distributions between categories.



11. Total Profit by Region

The notebook groups the data by Region and calculates total profit:

region_profit = df.groupby("Region")["Profit"].sum()



12. Profit by Region and Category

A grouped bar plot is created to compare profit across regions and categories.



13. Discount vs Profit

A scatter plot is used to study the relationship between discount and profit.



14. Discount vs Average Profit

The notebook calculates average profit for each discount level:

discount_profit = df.groupby("Discount")["Profit"].mean()

A line plot is then created.



15. Correlation Analysis

The numerical columns used for correlation are:

numeric_data = df[
    ["Sales", "Quantity", "Discount", "Profit"]
]

The correlation matrix is calculated using:

correlation = numeric_data.corr()

16. Correlation Heatmap

A heatmap is created to visualize the correlations between the numerical attributes.



Output Visualizations

The project includes the following output images:

Profit Distribution

Sales Distribution

Total Profit by Category

Total Profit by Sub-Category

Profit Distribution by Category

Total Profit by Region

Profit by Region and Category

Discount vs Profit

Discount vs Average Profit

Correlation Heatmap

How to Run

Using Google Colab

Open the task2_EDA.ipynb notebook in Google Colab.

Upload superstore_raw.csv.

Run the cells from top to bottom.

Check the generated charts and analysis outputs.

Using Jupyter Notebook

Install the required libraries:

pip install pandas matplotlib seaborn jupyter

Place superstore_raw.csv in the appropriate location.

Update the CSV path if required.

Open task2_EDA.ipynb.

Run all cells.

Project Structure

Task2_EDA/
│
├── task2_EDA.ipynb
├── README.md
│
└── outputs/
    ├── profit_distribution.png
    ├── sales_distribution.png
    ├── profit_by_category.png
    ├── profit_by_subcategory.png
    ├── profit_distribution_by_category.png
    ├── profit_by_region.png
    ├── profit_by_region_category.png
    ├── discount_vs_profit.png
    ├── discount_vs_average_profit.png
    └── correlation_heatmap.png

Conclusion

This EDA notebook provides visual analysis of retail sales and profit data. It covers data preparation, distribution analysis, category and region comparisons, discount-profit analysis, and correlation analysis using Python visualization libraries.
