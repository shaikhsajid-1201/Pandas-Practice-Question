# How to Spot Duplicate Patterns in Your Data – The Smart Way Using Pandas!

**Question:**  
"Imagine you’re working with a dataset containing user activity logs, and you want to find users who performed the same action more than once on the same day. How would you efficiently identify these duplicates using Pandas?"  

**DataFrame (Sample Dataset):**  
```python
import pandas as pd

# Sample data
data = {'User_ID': [101, 102, 101, 103, 101, 102, 104],
        'Action': ['Login', 'Upload', 'Login', 'Download', 'Login', 'Upload', 'View'],
        'Date': ['2023-12-19', '2023-12-19', '2023-12-19', '2023-12-19', '2023-12-19', '2023-12-19', '2023-12-19']}

df = pd.DataFrame(data)
print(df)
```

**What You Will Learn:**  
- How to identify duplicate records across multiple columns  
- Using Pandas' `duplicated()` method effectively  
- Techniques to filter and group duplicate patterns  

**Explanation to Solve the Question:**  
Here’s how you can solve it step by step:  

```python
# Step 1: Identify duplicates based on 'User_ID', 'Action', and 'Date'
duplicates = df[df.duplicated(subset=['User_ID', 'Action', 'Date'], keep=False)]

# Step 2: Group duplicates to check patterns
grouped_duplicates = duplicates.groupby(['User_ID', 'Action', 'Date']).size().reset_index(name='Count')

# Step 3: Filter groups with more than one occurrence
result = grouped_duplicates[grouped_duplicates['Count'] > 1]
print(result)
```  

**CTA (Call-to-Action):**  
"Have you come across duplicate patterns in your data? How did you handle them? Share your methods below! Don’t forget to follow me for more unique and practical Pandas challenges to enhance your data analysis skills!"  
