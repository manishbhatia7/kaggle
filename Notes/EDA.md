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
categorical_variables=['HomePlanet','CryoSleep','Destination','VIP']
fig=plt.figure(figsize=(10,16))
for i, var_name in enumerate(categorical_variables):
    ax=fig.add_subplot(4,1,i+1)
    sns.countplot(data=train, x=var_name, axes=ax, hue='Transported')
    ax.set_title(var_name)
fig.tight_layout()  # Improves appearance a bit
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
### Piechart for target distribution
```
train['Transported'].value_counts().plot.pie(explode=[0.1,0.1],autopct='%1.1f%%',shadow=True,textprops={'fontsize':16}).set_title('Target Distribution')
```

### Distribution of Numerical Variables
```
for i, var_name in enumerate(exp_feats):
    # Left plot
    ax=fig.add_subplot(5,2,2*i+1)
    sns.histplot(data=train, x=var_name, axes=ax, bins=30, kde=False, hue='Transported')
    ax.set_title(var_name)
    
    # Right plot (truncated)
    ax=fig.add_subplot(5,2,2*i+2)
    sns.histplot(data=train, x=var_name, axes=ax, bins=30, kde=True, hue='Transported')
    plt.ylim([0,100])
    ax.set_title(var_name)
fig.tight_layout()  # Improves appearance a bit
plt.show()
```
### Creating the age group buckets
```
train.loc[train['Age']<=12,'Age_Group']='Age_0-12'
train.loc[train['Age']>12,'Age_Group']='Age_13-17'
```

### Depicting Missing Values
```
na_cols=data.columns[data.isnull().any()].tolist()
mv=pd.DataFrame(data[na_cols].isna().sum(),columns=['Missing Column'])
mv['Percentage Missing']=np.round(100*mv['Missing Column']/len(data),2)

```