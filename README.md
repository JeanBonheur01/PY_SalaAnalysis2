# PY_SaleAnalysis2

## Table of contents

- [Problem Statement](problem-statement)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Exploratory (Descriptive) dataanalysis](#exploratory-(descriptive)-dataanalysis)
- [Questions and PY codes](questions-and-py-codes)
- [Results/Findings](#resultsfindings)
- [Recommendations & Conclusion](#recommendations)

### Problem Statement

The company's sales dataset is huge and contains some data that can be analysed to extract some valuable information. The purpose of this project was to conduct an exploratory data analysis to describe trends and important factors occurring in the company's sales dataset. The objective was to present the data in a more easily understandable way through various descriptive statistics and visualizations.

### Data Sources

The primary data used for this analysis were large Excel datasets. These datasets were imported from a local repository to the analysis platform, where they were checked and prepared for analysis.

### Tools

- Visual Studio Code: The tool is a code editor optimized for building and debugging modern web and cloud applications. It integrates different code editors, such as Python and Jupyter Notebooks, which were activated/enabled to conduct this analysis within Visual Studio Code.  [Find here](https://code.visualstudio.com/)

- The analysis was conducted using the functionalities of Python's pandas, seaborn and Matplotlib.
  
### Exploratory (Descriptive) dataanalysis  

Here, only some interesting questions are highlighted. To view all the questions that were analyzed and answered in the analysis, check the Ipynb_file in the files section.

### Questions and PY codes

1. What is the overall sales trend monthly?

```py
df['order_date'] = pd.to_datetime(df['order_date'])
df['month_year'] = df['order_date'].dt.to_period('M').astype(str)

df_monthly_trend= df.groupby("month_year")['sales'].sum().reset_index()

plt.figure(figsize=(15, 6)) 
plt.plot(df_monthly_trend['month_year'], df_monthly_trend ['sales'])
plt.xlabel('Month-Year') 
plt.ylabel('Sales')      
plt.title('Monthly Sales Trend')  
plt.grid(True) 
plt.xticks(rotation='vertical', size = 8) 
plt.tight_layout()  
plt.show()
```
![Monthly_Sales_Trend](https://github.com/user-attachments/assets/093c3935-1cd6-4724-9f60-9f8221b2cece)

2. What is the most prefered ship mode?

```py
ship_mode= df.groupby("ship_mode").size()

plt.figure(figsize=(10, 6))

sns.countplot(x=df['ship_mode'], hue=df['ship_mode'], palette='viridis', dodge=False)

plt.title('Distribution of Preferred Shipping Modes')
plt.xlabel('Shipping Mode')
plt.ylabel('Count')
plt.show()
```
![Distribution_od_Preferred_Shipping_Modes](https://github.com/user-attachments/assets/c71008bf-4487-4b56-bdab-a31ddcbe7b9e)

3. Which are the most profitable category and sub-category?

```py
category_profit= df.groupby("category")["profit"].sum()
category_profit_sort= category_profit.sort_values(ascending=True).reset_index()

plt.figure(figsize=(10, 6))

sns.barplot (x='category', y='profit', data= category_profit_sort, hue= 'category', palette='viridis', dodge= False)

plt.title('Total Profit by Category')
plt.xlabel('Categoty')
plt.ylabel('Total Profit')
plt.show()
```
![Total_Profit_Category](https://github.com/user-attachments/assets/9017a6da-b8b7-4dfc-abda-b603bfb60fc4)

```py
sub_category_profit= df.groupby("sub_category")["profit"].sum()
sub_category_profit_sort= sub_category_profit.sort_values(ascending=True).reset_index()

plt.figure(figsize=(10, 6))

sns.barplot (x='sub_category', y='profit', data= sub_category_profit_sort, hue= 'sub_category', palette='Set2', dodge= False)

plt.title('Total Profit by Sub_Category')
plt.xlabel('Sub_Categoty')
plt.ylabel('Total Profit')
plt.xticks(rotation=45, ha='right') 
plt.show()
```
![Total_Profit_SubCategory](https://github.com/user-attachments/assets/878394a7-0d28-4eec-aa48-06262108845e)

### Results/Findings

1. The analysis shows that sales are initially low at the beginning of each year, but after four months, they start to rise significantly. Sales also decrease in July each year, but then begin to increase again, reaching a peak at the end of the year.

2. The most preferred shipping mode is 'Standard Class,' followed by Second Class, First Class, and lastly, Same Day.

3. The most profitable category is Technology, followed by Office Supplies, and lastly, Furniture. Within each category, different subcategories show varying profitability, with Copiers being the most profitable, followed by Phones, Bookcases, and others. The only subcategory that registered a loss is Tables.

### Recommendations & Conclusion

The company must take into consideration the analysis findings, where some products sell better and are more profitable than others, along with preferred shipping modes and the most profitable categories and subcategories. This can help the company adjust its sales and promotions to enhance the overall sales processes. Further diagnostic analysis may be needed to gain a deeper understanding of why certain trends occur, which can help address them more effectively.

💻🖱️💻🖱️💻



