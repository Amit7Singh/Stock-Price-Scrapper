# CsBda MiniProject Pre-Work

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


# CODE 1

import matplotlib.pyplot as plt


from alpha_vantage.timeseries import TimeSeries

ts = TimeSeries(key='P68VZ6AIIS7K8Z21', output_format='pandas')
data, meta_data = ts.get_intraday(symbol='GOOGL',interval='1min', outputsize='full')
X1=data.iloc[:,3]

ts = TimeSeries(key='P68VZ6AIIS7K8Z21', output_format='pandas')
data, meta_data = ts.get_intraday(symbol='INFY',interval='1min', outputsize='full')
X2=data.iloc[:,3]

ts = TimeSeries(key='P68VZ6AIIS7K8Z21', output_format='pandas')
data, meta_data = ts.get_intraday(symbol='AMZN',interval='1min', outputsize='full')
X3=data.iloc[:,3]

ts = TimeSeries(key='P68VZ6AIIS7K8Z21', output_format='pandas')
data, meta_data = ts.get_intraday(symbol='FB',interval='1min', outputsize='full')
X4=data.iloc[:,3]


plt.axis([0,2000 , min(X1)-1, max(X1)+1])
#plt.figure(figsize=(5,5))

i=0
for i in range(2000):
    temp_y1 = X1[i]
    plt.subplot(2, 2, 1)
    plt.scatter(i, temp_y1)
    plt.title('Google')


    temp_y2 = X2[i]
    plt.subplot(2, 2, 2)
    plt.scatter(i, temp_y2)
    plt.title('Infosys')


    temp_y3 = X3[i]
    plt.subplot(2, 2, 3)
    plt.scatter(i, temp_y3)
    plt.title('WallMart')

    temp_y4 = X4[i]
    plt.subplot(2, 2, 4)
    plt.scatter(i, temp_y4)
    plt.title('Amazon')

    plt.pause(1)

plt.show()



# CODE 2
import pandas as pd
import matplotlib.pyplot as plt


dataset1=pd.read_csv("C:/Users/HP/Desktop/BDA PROJECT/FaceBookHistoricalQuotes.csv")
dataset2=pd.read_csv("C:/Users/HP/Desktop/BDA PROJECT/WalmartHistoricalQuotes.csv")
y1=dataset1.iloc[:,1]
y2=dataset2.iloc[:,1]

plt.figure(figsize=(5,5))
plt.subplot(2,1,1)
plt.plot(y1,'r')
plt.title('AAPL')

plt.legend()


plt.subplot(2,1,2)
plt.plot(y2,'b')
plt.title('WMT')

plt.legend()

plt.show()
