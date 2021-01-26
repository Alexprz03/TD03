# TD03 - Alec GUESSOUS - Alexandre PEREZ

## Blockchain programming - Call API Coinbase

### Topic
***
#### Prerequisites
* Use Python 3
* No precompiled module, write the REST calls yourself
* Use Binance or Coinbase
* Create a function for each task

***
#### Tasks list - GET
* Create a git repository and share it with the teacher
* Get a list of all available cryptocurrencies and display it
* Create a function to display the ’ask’ or ‘bid’ price of an asset. Direction and asset name as parameters:
'''
   def getDepth(direction='ask', pair = 'BTCUSD')
'''
* Get order book for an asset
* Create a function to read agregated trading data (candles)
'''
   def refreshDataCandle(pair = 'BTCUSD', duration = '5m’)
'''
* Create a sqlite table to store said data (schema attached in the next slide)
* Store candle data in the db
* Modify function to update when new candle data is available
* Create a function to extract all available trade data
'''
   def refreshData(pair = 'BTCUSD’)
'''
* Store the data in sqlite

***
#### Tasks list - POST

* Create an order
'''
   def createOrder(api_key, secret_key, direction, price, amount, pair = 'BTCUSD_d', orderType = 'LimitOrder’)
'''
* Cancel an order
'''
   def cancelOrder(api_key, secret_key, uuid)
'''

***
#### Keeping track of updates:
'''
   CREATE TABLE last_checks(Id INTEGER PRIMARY KEY, exchange TEXT, trading_pair TEXT, duration TEXT, table_name TEXT, last_check INT, startdate INT, last_id INT);
'''

***
#### Data candles:
'''
   setTableName = str(exchangeName + "_" + pair + "_" + duration)
   tableCreationStatement = """CREATE TABLE """ + setTableName + """(Id INTEGER PRIMARY KEY, date INT, high REAL, low REAL, open REAL, close REAL, volume REAL, quotevolume      REAL, weightedaverage REAL, sma_7 REAL, ema_7 REAL, sma_30 REAL, ema_30 REAL, sma_200 REAL, ema_200 REAL)"""
'''

***
#### Full data set:
'''
   setTableName = str(exchangeName + "_" + pair)
   tableCreationStatement = """CREATE TABLE """ + setTableName + """(Id INTEGER PRIMARY KEY, uuid TEXT, traded_btc REAL, price REAL, created_at_int INT, side TEXT)""”
'''

***
### References
* [Wikipedia page for APIs](https://fr.wikipedia.org/wiki/Interface_de_programmation)
* [Using requests in Python](https://www.pythonforbeginners.com/requests/using-requests-in-python)
* [Binance API Documentation](https://github.com/binance-exchange/binance-official-api-docs/blob/master/rest-api.md)
* [Coinbase pro API documentation](https://docs.pro.coinbase.com/)

