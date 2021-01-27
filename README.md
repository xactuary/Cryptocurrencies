# Cryptocurrencies
 
###  Data Cleaning

The data cleaning steps used are:
1.  Removed all "IsTrading" values that are False.  So only kept coins being traded.
2.  Removed all those that do not have a working algorithm.  This was determined by looking at the "totalCoinsMined".  If this value was NaN that means the algorithm isn't working so the row is removed.  
3.  Removed the column "IsTrading" since it is no redundant.
