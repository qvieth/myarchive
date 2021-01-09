# Relational Databases for Data Science/Analysis - Understanding relational databases and SQL data types

## Contents

- [Relational Databases for Data Science/Analysis - Understanding relational databases and SQL data types](#Relational Databases for Data Science/Analysis - Understanding relational databases and SQL data types)
- [Introduction](#Introduction)
- [Structured Data](#Structured Data)
- [Databases](#Databases)
    - [data science pipeline](#Databases#data science pipeline)
- [Relational Databases](#Relational Databases)
    - [Customer Table](#Relational Databases#Customer Table)
    - [Entity Relationship Diagram](#Relational Databases#Entity Relationship Diagram)
- [Relational Database Management Systems](#Relational Database Management Systems)
    - [SQL](#Relational Database Management Systems#SQL)
        - [MySQL](#Relational Database Management Systems#SQL#MySQL)
        - [PostgreSQL](#Relational Database Management Systems#SQL#PostgreSQL)
        - [Oracle DB](#Relational Database Management Systems#SQL#Oracle DB)
        - [SQL Server](#Relational Database Management Systems#SQL#SQL Server)
        - [SQLite](#Relational Database Management Systems#SQL#SQLite)
    - [SQLite Data Types](#Relational Database Management Systems#SQLite Data Types)
    - [Takeaways](#Relational Database Management Systems#Takeaways)

# Introduction
- One of the __most important questions__ to address especially when __acquiring large amounts of data__ is :
    - __where__ will all the data be stored?
- __Data storage__ is such an integral part of __data acquisition__
- We should understand the __type of data__ when acquiring data :
    - structured
    - semi-structured
    - unstructured
- Unstructured data is data that has __no defined organization__ or __data model__
    - It is the photos, posts, videos, PDF files, and Word documents that can contain a wide range of __dimensions__ and __types__
    - It is estimated that by 2017, nearly 80% of the 125 exabytes of global business data was unstructured
- Semi-structured data has more organization than unstructured data, an example being XML data which is stored in only plain text format
    - Here is an example of the [sitemap](https://yoast.com/what-is-an-xml-sitemap-and-why-should-you-have-one/) for codecademy.com which is an XML file that stores all of the links found on the Codecademy home page
```xml
<sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" xmlns:xhtml="http://www.w3.org/1999/xhtml">
  <sitemap>
    <loc>https://www.codecademy.com/sitemap_static.xml</loc>
  </sitemap>
  <sitemap>
    <loc>https://www.codecademy.com/sitemap_catalog.xml</loc>
  </sitemap>
  <sitemap>
    <loc>https://www.codecademy.com/sitemap_article.xml</loc>
  </sitemap>
  <sitemap>
    <loc>https://www.codecademy.com/sitemap_module.xml</loc>
  </sitemap>
  <sitemap>
    <loc>https://www.codecademy.com/sitemap_skills_v2.xml</loc>
  </sitemap>
  <sitemap>
    <loc>https://www.codecademy.com/sitemap_paths.xml</loc>
  </sitemap>
  <sitemap>
  <loc>https://www.codecademy.com/sitemap_references.xml</loc>
  </sitemap>
</sitemapindex>
```
- In this lesson, we will focus on __structured data__, as it is the data found within __relational databases__

# Structured Data
- __Structured data__ is the most __organized__ type of data
- It follows a __data model__, which is a kind of blueprint that defines and describes the structure of the data
- __Structured data__ is typically in the form of __tables__ that are well defined by their rows and columns
- a great example being a __DataFrame__ from the popular Python library __pandas__
- Some advantages of structured data are that its __explicit structure__ aids in organized storage and accessibility
- This also allows it to be __easily indexed__ for efficient reference
- With structured data, we are able to __set permissions__ for __security purposes__
- so that only those that meet __predetermined guidelines__ and __clearances__ can access the data
- Examples of structured data are:
    - Online forms
    - Excel Spreadsheets
    - SQL Databases

# Databases
- In many applications, the __amount of data__ collected is __vast__ and can not be stored in a single machine
- This is why __databases__ are so vital when working with certain data
- Databases are __collections of data__ that are __organized__ for efficient accessibility and management
- __Data Analysts__ use databases for __marketing, business, and sales__
- __Data Scientists, Software Engineers__, and __Web Developers__ use databases to store the large amounts of data that are often used in production scale applications
- Within the __data science pipeline__, __databases__ are considered the __storage units__ that house the data so it can be cleaned for analysis and modeling

## data science pipeline
- The __Data Science Pipeline__ :
    - __Storage__ - where the data is __housed__ throughout the entire __data science life cycle__
    - __Data Cleaning__ - assigning proper data types and categories, removing duplicate and null values within the data
    - __Anomaly removal__ - removal of any data points that would worsen the __modeling performance__
    - __Transformation__ - applying changes to every data point to __improve modeling performance__
    - __Augmentation__ - changing the size of data used for __training a model__, such as cropping, rotating, or flipping an image

- There are multiple __database models__ that specify how a database is structured
    - For instance, the __flat model__ is the most simple and is essentially a table
    - The __relational model__ can be viewed as a __database model__ that has multiple tables that each describe a particular __entity__ of the database
- We refer to the databases that follow the __relational model__ as __relational databases__

# Relational Databases
- Relational databases are the __primary__ means of storage for __structured data__
- These databases are relational because they organize data into __tables__ that each contain data related to one another
- tables are composed of rows and columns :
    - __rows__ represents __each individual observation__ called a __record__
    - __columns__ represents the __characteristics__ or __dimensions__ of the record called __fields__

## Customer Table

| customer_id | first_name | last_name | phone_number | email                  | address_id |
|-------------|------------|-----------|--------------|------------------------|------------|
| 1000        | edgar      | smith     | 123-441-5225 | edgar_smitty@email.com | 234        |
| 1001        | taylor     | baile     | 123-521-6547 | tb123@email.com        | 544        |
| 1002        | victor     | thompson  | 123-968-0023 | music_lover@email.com  | 107        |
| 1003        | ingrid     | julius    | 123-352-5438 | ijulius@email.com      | 161        |

- An __image__ of a table with fields and records
- In this table we can see the 6 fields: 
  |1. CustomerID | 2. first_name | 3. last_name | 4. phone_number | 5. email | 6. address_id
- Each of these __fields__ is an __attribute of a record__
- For this particular view, we see 4 records in the table, with each representing a single customer
- Relational databases are so useful for data science and analytics
- because we often want to understand the __relationships__ among our data
- and relational databases organize data to make those relationships clear and simple to explore
- The tabular structure of relational databases also makes them easy to index, query, and scale
- When we consider relational databases as a collection of tables, what we call a __schema__
- we can visualize them with __entity-relationship diagrams__, which give us a chance to view the data within each table, and how each table relates to the others

## Entity Relationship Diagram
- An Entity Relationship Diagram
- In the entity-relationship diagram above we can see the seven tables that make up the relational database of a record store
- There are tables that contain information on customers, orders, albums, etc
- If we look closely, we can see that some of the tables are __related to each other__ by certain __fields__
- These shared fields are called __keys__ and are the __links__ that connect the various tables

# Relational Database Management Systems
- Another advantage of working with relational databases is Relational Database Management systems, or RDBMS
- Relational Database Management Systems (RDBMS) are important for data science and analytics
- because they provide the functionality needed for creating, reading, updating, and deleting data
- often referred to as __CRUD__ within our database
- The language that data teams utilize most often in RDBMS to execute commands is Structured Query Language (SQL), pronounced as “S-Q-L” or “sequel”
## SQL
- Structured Query Language (SQL) is one of the most common and powerful languages for querying databases
- It is fast, secure, and able to return millions of data points in just a few lines
- While there are hundreds of RDBMS, some of the most common RDBMS that use SQL are:
### MySQL
- MySQL is a popular free and open-source SQL database
- It is widely used for web applications because the MySQL Server is renowned for its speed, reliability, and ease of use on multiple platforms

### PostgreSQL
- Much like MySQL, PostgreSQL is a popular open-source SQL database
- PostgreSQl is one of the oldest RDBMS with over 30 years into its development
- so it has an extensive community supporting it and is known for its reliability and array of features

### Oracle DB
- Oracle is considered to be among the most popular of all RDBMS
- Owned by Oracle Corporation and __closed sourced__
- Oracle DB is the goto RDBMS for corporations as it is able to scale for and support their massive workloads effectively
- Licensing for Oracle DB however, is known to be expensive and can be infeasible to use for certain applications

### SQL Server
- SQL Server is another privately-owned RDBMS that is popular, especially among corporations
- While __Microsoft__ offers SQL Server free through its SQL Server 2019 Express edition
- the enterprise editions that are designed for large scale applications with more functionality become more expensive as your application scales

### SQLite
- SQLite is another popular open-source SQL database
- SQLite is designed to be compact, efficient, and self-contained
- SQLite is able to store a complete database in a single cross-platform disk file so that it is not necessary to connect databases to a server
- These characteristics and capabilities are what make SQLite considered to be the __most used RDBMS__
- as it is used in most cell phones, computers, and several other daily used devices
- Throughout our course, we will use SQLite for working with relational databases

- It is __important__ to note that while most RDBMS use SQL, the __SQL data types__ can ___vary between RDBMS__
- With this in mind, let’s get familiar with some of the data types found in SQLite

## SQLite Data Types
- With __unstructured data__, you would be able to enter __any data in any order__
- However, in a relational database, we are able to __restrict__ certain fields to a specific data type
- You may recall the various data types within Python, such as __integers, floats, strings,__ and __booleans__
- SQLite has __similar__ data types, but some of them go by __different names__
    - such as __VARCHAR__, SQL’s version of __string__
    - and __INTEGER__, the SQL version of __int__

Python and SQLite Data Types

| python | sqlite                                             |
|--------|----------------------------------------------------|
| str    | character(20)<br>varchar(255)<br>text              |
| int    | int<br>interger<br>smallint<br>mediumint<br>bigint |
| float  | real<br>double<br>double precision<br>float<br>    |
| bool   | bit                                                |

## Takeaways
- __Relational databases__ are collections of __structured data__ that utilize tables to maintain __relationships__ among data
- Tables within a relational database contain __fields__ and __records__, and the tables of a relational database are described by a __schema__
- There are several __relational database management systems__ that we can use to work with relational databases
- and most __RDBMS__ utilize __SQL__ to create, read, update, and delete data within the database
