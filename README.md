# BigData-NFT
Big Data project about NFT using the twint library to scrape tweets.


1) Open terminal and set directory as file with csv file
2) Open second terminal and find the hive-server container id using
          >docker ps
3) Go to root directory on the hive-server container and create folder named data
          >cd
          >mkdir data
4) Copy csv file to the data folder in hive-server 
          >docker cp NFT_EN_Clean.csv b1d3d6a1e506:root/data
5) Create directory inside hdfs 
          >hadoop fs -mkdir BigData
6) Put csv file into hdfs
          >hadoop fs -put NFT_EN_Clean.csv BigData
7) Start the hive-server
          >hive
8) Create a database named NFTdatabase
          hive> create database NFTdatabase;
9) Use the database NFTdatabase
          hive> use NFTdatabase;
10) Create table in database
          hive>create external table NFTtable(
               index int,
               id int,
               `date` DATE,
               `time` TIMESTAMP,
               tweet string,
               language string)
               row format delimited
               fields terminated by ',';
11) Load csv file into NFTtable
           hive> LOAD DATA INPATH 'BigData/NFT_EN_Clean.csv' INTO TABLE NFTtable;
