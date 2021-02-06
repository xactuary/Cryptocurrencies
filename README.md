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
6.  Kept only the rows where coins are mined.  I have assumed anything with a positive value for "TotalCoinsMined" meets this requirement.
```
    df_crypto_new = df_crypto_new[df_crypto_new['TotalCoinsMined']>0]
```
Note there is one row where the coins mined is negative which should not happen so this has been excluded. 

### MODEL

Using PCA, the dataframe is reduced to 3 principal components with the CryptoCurrenty abbreviation as the index.  When re-running PCA, the values change slightly so each run of the model may end up with slightly different results. 

The Variance ratio on the 3 components are:
```
array([0.02793073, 0.02139493, 0.02049771])
```
The PCA processed data is now run through the Kmeans algorithm to produce an Elbow Curve as shown below:

![](https://github.com/xactuary/Cryptocurrencies/blob/main/Resources/ElbowCurve.PNG)

This curve suggests that the number of clusters should be 4 because that is where the elbow curve starts to flatten out.


Kmeans is run and a new dataframe is created: 

![](https://github.com/xactuary/Cryptocurrencies/blob/main/Resources/Output_Del3.PNG)

The following 3D plot shows the 4 clusters graphed against the 3 PC Components

![](https://github.com/xactuary/Cryptocurrencies/blob/main/Resources/3Dplot.PNG)

the following table shows the tradable cryptocurrencies.

![]()

The total number of tradable cryptocurrencies is 532.

Scatter plot of results.  To plot the results, the data for TotalCoinsMined and TotalCoinSupply are scaled using the MinMaxScaler.  Otherwise the data would be way to variable to graph properly.  

![]()








