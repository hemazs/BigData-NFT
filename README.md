# BigData-Naruto
Big Data project about Naruto using the twint library to scrape tweets.


1) Open terminal and set directory as file with csv file
2) Open second terminal and find the hive-server container id using
          >docker ps
3) Go to root directory on the hive-server container and create folder named data
          >cd
          >mkdir data
4) Copy csv file to the data folder in hive-server 
          >docker cp NarutoClean1.csv b1d3d6a1e506:root/data
5) Create directory inside hdfs 
          >hadoop fs -mkdir root/data/BigData
6) Put csv file into hdfs
          >hadoop fs -put NarutoClean1.csv root/data/BigData
7) Start the hive-server
          >hive
8) Create a database named NarutoDB
          hive> create database NarutoDB;
9) Use the database NarutoDB
          hive> use narutodb;
10) Create table in database
          hive>create external table narutotable4(
               id int,
               `date` DATE,
               `time` TIMESTAMP,
               tweet string,
               language string)
               row format delimited
               fields terminated by ',';
11) Load csv file into narutotable4
           hive> LOAD DATA INPATH 'root/data/BigData/NarutoClean1.csv' INTO TABLE narutotable4;
