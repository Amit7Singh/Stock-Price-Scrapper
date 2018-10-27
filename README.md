# CsBda MiniProject

PROBLEM STATEMENT
1. Display the live market price of 4 different listed companies (of any exchange like NASDAQ, NSE etc) 
   in four different frames of a single view. In another view compare the historical market price (last 2 years)
   of any two companies using two frames. Find your own source of data. Sample Layout: 
   
   
 SOLUTION:
 
 1.As the question said that we have to use live market price of 4 different listed companies 
   so I choosen 1.AMAZON
                2.WALMART
                3.MICROSOFT
                4.FACEBOOK
 2.We have to choose any exchange like NASDAQ, NSE etc .
   So I choosen NASDAQ exchange
  
 3.In question it is said to display the live data 
   So I used alpha_vantage API to extract the live data of 4 different companies
   we use ->  "from alpha_vantage.timeseries import TimeSeries"
   to import alpha vantage time series to extract data on run time
   I chossen the interval of 1 min
 
 4.Extracted data contain 5 column named "CLOSE", "VOLUME", "OPEN", "HIGH", "LOW"  along with date. 
 
 5.I choosen the "CLOSE" column data for line graph representation because  "CLOSE" can show the performance of company.
 
 6.For comparative study I plotted the graphs of above 4 companies together in a single view.
   
 Question also said to compare the historical market price of last 2 year of any 2 company using two frame 
 -> for this I download the 2 year data of "WALMART" and "AMAZON" from "WWW>nasdaq.com"
    and used it for further line graph representation.
