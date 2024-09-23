# PY_SalaAnalysis2

## Table of contents

- [Problem Statement](problem-statement)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Exploratory (Descriptive) dataanalysis](#exploratory-(descriptive)-dataanalysis)
- [Questions and PY codes](questions-and-py-codes)
- [Results/Findings](#resultsfindings)
- [Recommendations](#recommendations)
- [Conclusion](#conclusion)

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

### Results/Findings

### Recommendations

### Conclusion 



