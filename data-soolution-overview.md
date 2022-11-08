# Data Solution Overview
In our Hey Blue! system we have different types of data that need different storages

* General data (User data, connection history, stores, etc.)
* Fast changing data with short TTL (location data)
* Analytics for different interactions with platform

## General data
General data is very important for us since it stores user information, acquired points and similar information. For it we decided to use relational database. Our data is not highly connected so there will be no extra joins that could slow down performance. Also we don't expect changes in our tables.
 ![Relational database](https://cdn.iconscout.com/icon/premium/png-256-thumb/relational-database-2417424-2036371.png)

 ## Location data
 Location data is temporary data that will change frequently and it has to have short TTL (eg. 15 minutes). It has to be available almost instantly so we would like to keep it in our RAM instead of disk. To store location we decided to use in memory Redis as database with configured data TTL.

![Redis](https://dwglogo.com/wp-content/uploads/2017/12/1100px_Redis_Logo_01.png)

## Analytics
Since we are using third party analytics to process them, [ADR-5](./ADRs/ADR-005.md), we only need to forward them all data that we want processed. All interactions on platform will we sent to AWS SQS so that our analytics service can forward them all to processing.

![AWS SQS](https://seeklogo.com/images/A/aws-sqs-simple-queue-service-logo-8884A71ECB-seeklogo.com.png)