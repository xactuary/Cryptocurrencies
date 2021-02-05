# Cryptocurrencies
 
###  Data Cleaning

The data cleaning steps used are:
1.  Removed all "IsTrading" values that are False.  So only kept coins being traded.
    ```
    df_crypto.drop(df_crypto[df_crypto['IsTrading']==False].index,inplace=True)
    ```
2.  Removed all those that do not have a working algorithm.  This was determined by looking at the "totalCoinsMined".  If this value was NaN that means the algorithm isn't working so the row is removed.  
```
    df_crypto.drop(df_crypto[df_crypto['Algorithm']=='NaN'].index,inplace=True)
```
3.  Removed the column "IsTrading" since it is now redundant.
```
    df_crypto = df_crypto.drop(['IsTrading'],axis=1)
```
4.  Removed all rows that have at least 1 null value.
```
    for column in df_crypto.columns:
        print(f"Column {column} has {df_crypto[column].isnull().sum()} null values")    
```
5.  dropped the NaN values
```
    df_crypto_new = df_crypto.dropna()
```
