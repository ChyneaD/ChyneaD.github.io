### Data Cleaning in EDA


```
# Indexing our rt list by value, assigning this to variable x
x = rt.index(1.517088266)
# popping the x variable (our unwanted outlier)
rt.pop(x)
# popping the same index value from our error list
err.pop(x)
# we used this to round the next slowest(largest) rt by two decimal points 
print(round(max(rt),2))
print("rt len is " +  str(len(rt)) + " err len is " + str(len(rt)))
```

#### It's also possible to clean data from dataframes. Either by dropping non-existent values:


```
# Dropping empty values can be done by:
# Start by reading in csvfiles
df = pd.read_csv('')
df.dropna()
```

##### Or by making the dataframe not equal to a specific unique value.


```
# Finding the unique values
df['column'].unique()
# Indexing the dataframe with a specific column, and setting the dataframe to be not equal to a specific value
df = df[df.column != 'specific_value']

```
