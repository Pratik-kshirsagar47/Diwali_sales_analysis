# Diwali_sales_analysis

This project involves the analysis of a dataset containing Diwali sales data. The primary goal is to gain insights into customer demographics, purchasing behavior, and sales trends using data visualization techniques. We use Python libraries such as Pandas, Seaborn, and Matplotlib to perform data cleaning, manipulation, and visualization.

Dataset Overview
The dataset consists of 11,251 entries and 13 columns (after cleaning), which include:

User_ID: Unique identifier for customers
Cust_name: Customer name
Product_ID: Unique identifier for products
Gender: Gender of the customer
Age Group: Customer's age group
Age: Customer's age
Marital_Status: 1 for married, 0 for unmarried
State: State from which the customer placed the order
Zone: Geographical zone corresponding to the state
Occupation: Customer's occupation
Product_Category: Category of the product purchased
Orders: Number of orders placed
Amount: Total amount spent by the customer
After initial analysis, two columns (Status and unnamed1) containing null values were dropped from the dataset.

Data Preprocessing
Handling Missing Values:

The dataset had 12 missing values in the Amount column, which were removed using dropna().
The data type of Amount was converted from float to integer for consistency.
Renaming Columns:

The column Marital_Status was renamed to Shaadi to make it more readable.
Summary Statistics:

Basic statistics of numerical columns (Age, Orders, Amount) were generated using the describe() method.
Data Visualization
1. Gender-wise Sales Distribution
Using a count plot and a bar plot, the data shows that:

The majority of buyers are female.
Females also have a higher purchasing power compared to males.
python
Copy code
sns.countplot(x='Gender', data=df)
python
Copy code
sales_gen = df.groupby(['Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.barplot(x='Gender', y='Amount', data=sales_gen)
2. Age Group and Gender Sales Analysis
A count plot with a hue for gender shows that:

Most buyers belong to the 26-35 age group, with a higher concentration of female buyers.
python
Copy code
ax = sns.countplot(data=df, x='Age Group', hue='Gender')
for bars in ax.containers:
    ax.bar_label(bars)
3. Marital Status and Sales
A count plot and bar plot show the purchasing behavior based on marital status, with females again leading in both categories (married and unmarried).

python
Copy code
ax = sns.countplot(data=df, x='Marital_Status')
for bars in ax.containers:
    ax.bar_label(bars)
python
Copy code
sales_state = df.groupby(['Marital_Status', 'Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)
sns.barplot(data=sales_state, x='Marital_Status', y='Amount', hue='Gender')
4. State-wise Orders and Sales
A bar plot highlights the top 10 states with the highest number of orders and total sales, showing significant regional variation.

python
Copy code
sales_state = df.groupby(['State'], as_index=False)['Orders'].sum().sort_values(by='Orders', ascending=False).head(10)
sns.set(rc={'figure.figsize':(15,7)})
sns.barplot(data=sales_state, x='State', y='Orders')
python
Copy code
sales_state = df.groupby(['State'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False).head(10)
sns.barplot(data=sales_state, x='State', y='Amount')



Key Insights
Gender: Female customers outnumber male customers in terms of both the number of purchases and total amount spent.
Age Group: The majority of buyers are from the 26-35 age group.
Marital Status: Both married and unmarried customers contribute significantly to sales, with females leading in both categories.
Regional Sales: States like Maharashtra and Karnataka have the highest number of orders and sales.
Tools and Libraries
Pandas: Data manipulation and analysis
Seaborn: Statistical data visualization
Matplotlib: Plotting graphs
NumPy: Numerical computing
How to Run
Install the required libraries:
bash
Copy code
pip install pandas seaborn matplotlib numpy
Download the dataset and place it in the same directory as the script.
Run the Python script in a Jupyter Notebook or any Python environment.
Conclusion
This analysis provided useful insights into the sales patterns during the Diwali season. By leveraging the power of data visualization, businesses can better understand customer demographics and target their marketing strategies accordingly.

