# Stock Market Real-Time Data Analytics Pipeline on AWS

## ☁️ Project Overview
#### This project demonstrates how to build a real-time stock market analytics pipeline using AWS’s fully managed, serverless services. The pipeline is capable of streaming, processing, storing, analyzing, and alerting on stock data with minimal operational overhead.

![Architecture Diagram](https://imgur.com/dHXxUMX.png)


## A Python script continuosly fetches real-time stock market data from APIs like yfinance and pushes it to Amazon Kinesis Data Streams
![Python in Vscode](https://imgur.com/aY17eF8.png)
![Python in Vscode](https://imgur.com/dkTipwp.png)



## Amazon Kinesis Data Streams acts as a real-time data pipeline
![Python in Vscode](https://imgur.com/oA07Vlu.png)

![Python in Vscode](https://imgur.com/pfP4WBH.png)



## AWS Lambda function is triggered by kinesis to process, clean and transform the incoming data before storing in S3 and DynamoDB
![Python in Vscode](https://imgur.com/DkPddLM.png)

![Python in Vscode](https://imgur.com/0NtD6Yd.png)

![Python in Vscode](https://imgur.com/6SW32ah.png)


## The raw stock data is stored in Amazon S3 for historical analysis
![Python in Vscode](https://imgur.com/ySIJX6J.png)



## AWS Glue Data Catalog crawls the raw data stored in S3 , creating a structured schema that enables quering using Athena.
![Python in Vscode](https://imgur.com/3pJ1o2u.png)



## Amazon Athena, a serverless SQL query engine, runs analytical queries over the structured stock data via the Glue Data Catalog.

![Python in Vscode](https://imgur.com/1FSuttF.png)


## Amazon DynamoDB stores processed stock data for real-time lookups
![Python in Vscode](https://imgur.com/lM4tn66.png)


## An AWS Lambda function analyzes real-time stock trends by computing moving averages (SMA-5 and SMA-20) and detecting potential buy/sell signals.
![Python in Vscode](https://imgur.com/R4OsDqU.png)
  

## Amazon SNS sends real-time stock trend alerts via Email/SMS to users

![Python in Vscode](https://imgur.com/VbJTU8Z.png)

![Python in Vscode](https://imgur.com/MM95n7s.png)


## Clean-up
#### 1. Delete Kinesis Data Stream:
Navigate to the AWS Kinesis Console → Data Streams. Select the stock market data stream and click Delete.

#### 2. Delete Lambda Functions:
Open the AWS Lambda Console. Select the functions (`ProcessStockData`, `StockTrendAnalysis`). Click Delete and confirm the action.

#### 3. Delete DynamoDB Table:
Go to the DynamoDB Console. Select the `stock-market-data` table. Click Delete Table and confirm.

#### 4. Delete SNS Topic and Subscriptions:
Open the AWS SNS Console → Topics. Select the `Stock_Trend_Alerts` topic. Click Delete to remove the topic and its subscriptions.

#### 5. Delete S3 Buckets:
Navigate to the S3 Console. Select the bucket storing stock data and Athena query results. Empty the bucket first, then delete it.

#### 6. Delete Athena Tables and Queries:
Open the AWS Athena Console. Delete any tables and queries created for stock data.

#### 7. Delete IAM Roles and Policies:
Remove any IAM roles or policies specific to this project.

#### NOTE:

This project implements a near real-time data analytics pipeline rather than a fully real-time system. The stock data is streamed, processed by AWS Lambda, and stored in DynamoDB with a **30-second delay**.
