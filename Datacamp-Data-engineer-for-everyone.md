# Datacamp Data engineer for everyone

## Contents

- [Datacamp Data engineer for everyone](#Datacamp Data engineer for everyone)
    - [Data pipeline](#Datacamp Data engineer for everyone#Data pipeline)
    - [storing data](#Datacamp Data engineer for everyone#storing data)
        - [data structures](#Datacamp Data engineer for everyone#storing data#data structures)
        - [SQL databases](#Datacamp Data engineer for everyone#storing data#SQL databases)
        - [data warehouses and data lakes](#Datacamp Data engineer for everyone#storing data#data warehouses and data lakes)
        - [processing data](#Datacamp Data engineer for everyone#storing data#processing data)
        - [scheduling data](#Datacamp Data engineer for everyone#storing data#scheduling data)
        - [parallel computing](#Datacamp Data engineer for everyone#storing data#parallel computing)
        - [cloud computing](#Datacamp Data engineer for everyone#storing data#cloud computing)

## Data pipeline

-   think of the model of oil to kerosense or ...
-   O in OSEMN :
    -   Ingest
    -   Process
    -   Store
    -   Need Pipelines
    -   Automate flow from one station to the next
    -   Provide up-to-date, accurate, relevant data
-   source from which we extract data :
    -   user's actions and listening history on the mobile, desktop, website
    -   also internally data : HR management system and for payroll and benefits
-   the data is ingested into spotflix system
-   moving from their respective sources to our **data lake**
-   we then organize the data, moving it into the databases
    -   it could be artist data, like name, number of followers, and associated acts
    -   albums data like label, producer, year of release
    -   tracks data like name, length,...
    -   playlist data
    -   customer data
    -   employee data
-   in a nutshell, data pipelines ensure the data flows efficiently through the organization
    -   they automate :
        -   extracting
        -   transforming
        -   combining
        -   validating
    -   loading :
        -   human intervention
        -   errors
        -   times it takes for data to flow
-   ETL and data pipelines
    -   ETL :
        -   popular framework for designing data pipelines
        -   breaks up the flow of data into three sequential steps :
            -   E : extract data
            -   T : transforming extracted data
            -   L : load transformed data to another database
    -   Data pipelines :
        -   move data from one system to another
        -   may follow ETL (but not all the time, e.g. data may not be transformed and routed directly to applications like visualization tools or Saleforce)

## storing data

### data structures

fundamental concepts in data engineering

1.  structured data :

    -   easy to search and organize
    -   consistent model, rows and columns
    -   defined types(text, data or decimal)
    -   can be grouped to form relations
    -   stored in relational databases
    -   about 20% of the data is structured
    -   created and queried [query](query) using sql

2.  semi-structured data :

    -   resembles structured data, but allows more freedom
    -   relatively easy to organize and search
    -   consistent model, less-rigid implementation : different observations have different sizes
    -   different types
    -   can be grouped, but needs more work
    -   stored in NoSQL databases : JSON, XML, YAML

3.  unstructured data :

    -   does not follow a model, can't be contained in rows and columns
    -   difficult to search and organize
    -   usually text, sound, pictures or videos
    -   usually stored in data lakes, can appear in data warehouses or databases
    -   most of the data is unstructured
    -   can be extremly valuable
    -   because it's hard to search and organize
        -   this value could not be extracted until recently
        -   **with the advent of machine learning and artificial intelligence**
    -   adding some structure :
        -   use AI to search and organize unstructured data
        -   add information to make it semi-structured

### SQL databases

-   you can tell if someone is a data engineer or a data scientist just by asking how they use SQL!
    -   **data engineers** use SQL to create and maintain databases
    -   while **data scientists** use SQL to [query](query), filter, group and aggregate databases

```sql
Create table employees (
    employee_id INT,
    first_name VARCHAR(255),
    last_name VARCHAR(255),
    role VARCHAR(255),
    team VARCHAR(255),
    full_time BOOLEAN,
    office VARCHAR(255)
);
```

### data warehouses and data lakes

-   data lakes :
    -   stores all the raw data (can be petabytes
    -   cost-effective
    -   difficult to analyze
    -   used by data scientists for real-time analytics on big data
-   data warehouse :
    -   specific data for specific use
    -   relatively small
    -   store mainly structured data
    -   more costly to update
    -   optimized for data analysis
    -   used by data analysts and business analysts
    -   ad-hoc, read-only queries
-   **data catalog** for data lakes :
    -   what is the source of this data?
    -   where is this data used?
    -   who is the owner of this data?
    -   how often is this data updated
    -   good pratice in terms of data governance
    -   ensures reproducibility
    -   no catalog -> data swamp
-   => good practice for any data storage solution
    -   reliability
    -   autonomy
    -   scalability
    -   speed
-   database :
    -   general term
    -   loosely definedas organized data stored and accessed on a computer
-   data warehouse is a type of database
-   summary :
    -   data lakes
    -   data warehouses
    -   databases
    -   data catalog

### processing data

-   data processing : converting **raw data** into **meaningful information**
-   conceptually :
    -   remove unwanted data
    -   to save memory
    -   convert data from one type to another
    -   organize data
    -   to fit into a schema/structure
    -   increase productivity
-   how data engineers process data
    -   data manipulation, cleaning, and tidying tasks :
        -   that can be automated
        -   that will always need to be done
    -   store data in a sanely structured database
    -   create [views](views) on top of the database tables
    -   optimizing the performance of the database

### scheduling data
- manual vs time vs condition

-   scheduling can apply to any task we listed in the previous data processing lesson
-   to demonstrate scheduling, we will focus on :
    -   updating tables and databases to keep things straightforward and easy to understand
-   scheduling is the glue of your system
- holds each piece and organize how they work together
- run tasks in a specific order and resolves all dependencies

- manual, time and sensor scheduling
- there are different ways to glue things together :
    - run tasks manually
    - automation is when you set some tasks to execute at
        - a specific time
        - or condition ( this is called **sensor scheduling** )
    - manual and automated systems can also work together :
        - if a user manually upgrades their subscription tier on the app, automated tasks need to propagate this information to other parts of the system, to unlock new features and update billing information

- batches and streams :
- another thing that matters is how the data is ingested
    - batches :
        - group records and processed at intervals
        - often cheaper ( because you can schedule it when resources aren't being used elsewhere, typically overnight )
    - streams :
        - send individual records right away
- scheduling tools :
    - apache airflow
    - luigi

### parallel computing
- one term that's commonly used in data engineering is
    - **parallel computing** aka **parallel processing**
- basis of modern data processing tools
- necessary :
    - mainly because of memory
    - also for processing power
- how it works :
    - split tasks up into several smaller subtasks
    - distribute these subtasks over several computers
- benefits :
    - extra processing power
    - reduce memory footprint
- cons :
    - moving data incurs a cost
    - communication time

### cloud computing
- 
