# Quick Notes
### Check the Duplicates
```
print(f'Duplicates in Train Set: {train.duplicated().sum()}, ({np.round(100*train.duplicated().sum()/len(train),1)}%)')
```

### Checking any columns for nullity
```
missing_columns=data.columns[data.isnull().any()]
print(f"Missing columns are {missing_columns.tolist()}")
```

### Check the no of unique values in dataframe
```
unique_values_df=pd.DataFrame({'Column name':cat_cols,'No of Unique Values':[data[col].nunique() for col in cat_cols]})
```
### Distribution of categorical variables
```
fig,axes=plt.subplots(4,4,figsize=(20,16))
fig.suptitle('Distribution of Categorical Variables')
axes=axes.flatten()
for i,col in enumerate(unique_values_df['Column name']):
    sns.countplot(x=data[col],ax=axes[i],palette='coolwarm')
    axes[i].set_title(col,fontsize=4)
    axes[i].set_xlabel("Categorical Variable")
    axes[i].set_ylabel("Count")
    axes[i].tick_params(axis='x',rotation=45)
for j in range(i+1,len(axes)):
    fig.delaxes(axes[j])
plt.tight_layout(rect=[0,0,1,0.95])
plt.show()    
```
### Shapiro Normality Results
#### Applicable only for Numeric columns
```
print("Shapiro Normality Results")
for col in numerical_cols:
    stat,p=scipy.stats.shapiro(data[numerical_cols].dropna())
    if p > 0.05:
        print(f"{col} has passed normality test")
    else:
        print(f"{col} has not passed normality test")
```        