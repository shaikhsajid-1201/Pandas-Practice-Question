# How to Identify the Top Contributors in Your Data Using Pandas – The 80/20 Rule!

**Question:**  
"Have you ever wondered how to find the top 20% of products that make up 80% of your total sales in a large dataset? Let's solve this with Pandas!"

**DataFrame (Sample Dataset):**  
```python
import pandas as pd

# Sample data
data = {'Product': ['A', 'B', 'C', 'D', 'E'],
        'Sales': [15000, 25000, 5000, 10000, 30000]}

df = pd.DataFrame(data)
print(df)
```

**What You Will Learn:**  
- How to apply the Pareto Principle (80/20 rule) to real-world data
- Dynamic sorting and ranking techniques in Pandas
- How to calculate cumulative percentages and filter results based on thresholds

**Explanation to Solve the Question:**  
Let’s break it down:

```python
# Step 1: Sort the DataFrame by 'Sales' in descending order
sorted_df = df.sort_values(by='Sales', ascending=False)

# Step 2: Calculate the cumulative percentage of total sales for each product
sorted_df['Cumulative Sales'] = sorted_df['Sales'].cumsum()
total_sales = df['Sales'].sum()
sorted_df['Cumulative %'] = (sorted_df['Cumulative Sales'] / total_sales) * 100

# Step 3: Filter the top 20% of products contributing to 80% of the sales
result = sorted_df[sorted_df['Cumulative %'] <= 80]
print(result)
``` 
Have you used the Pareto Principle in your data analysis? What insights did you uncover? Share your experiences in the comments below! If you want more practical Pandas tips, follow me for daily challenges to boost your skills!
