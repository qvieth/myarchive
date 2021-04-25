# mynote

```
this should be empty
```

-   search keyword : glossary and terms
    -   https://www.workspace.co.uk/content-hub/entrepreneurs/glossary-of-business-terminology
    -   https://www.batimes.com/business-analyst-glossary-and-terms.html
    -   [145 keys BA concepts that you should know](https://medium.com/techcatch/145-key-business-analysis-concepts-that-you-should-know-e65d1736a964)
-   approach = way of dealing with something
-   At a minimum you should be familiar with Business Process Modeling and Requirements Management (including elicitation and gathering.) These are the core BA skills you will use almost anywhere you go
-   changes-contexts , needs-solutions, stakeholders-values
-   https://www.quora.com/How-does-one-go-about-becoming-a-business-analyst : must read before reading BABOK
    -   understand how business do and what they do : APQC PCF
        -   allows organizations to objectively track and compare
            -   their performance internally and externally
            -   with organizations from any industry
            -   standardize and document processes
            -   there's also industry's specific PCF
            -   It also would be a good idea to read up basic books
                -   on business strategy, marketing, finance, HR
                -   and operations
        -   https://www.youtube.com/watch?v=8FaEFSNcnHs : how organizations use PCF
-   https://en.wikipedia.org/wiki/Zachman_Framework : zachman framework
-   BMP : business management framework
-   https://www.quora.com/What-are-the-most-important-courses-to-be-a-good-business-analyst#!n=18 : second best after the previous link
-   analytics is about convincing (at scale)
-   BA :
    -   enabling change in enterprise by :
        -   defining needs and recommend solutions
            -   that deliver value to stakeholders
-   operation : logistics and supply chain
-   DataFrame s have 3 components :
    -   values
    -   column index
    -   and row index
-   `plt.style.use()`

-   constraints - give the data structure - 3 concepts :
    -   1. **attribute constraints** e.g. data types on columns (chapter 2)
    -   2. **key constraints** e.g. primary keys(chapter 3)
    -   3. **referential integrity constraints** enforced through foreign keys(chapter 4) - a record referencing another table must refer to an existing record in that table
    -   special attribute constraints :
        -   not-null and unique constraints
        -   keys and superkeys
    -   keys
    -   referential integrity
-   cartesian product of relations: https://www.youtube.com/watch?v=58i-sZ6h1mI
    -   the result is itself a relation
    -   its rows contain all of the columns from the combined relations
-   SQL joins are based on a mathematical notion called cartesian products
-   ERD part 2 lucid chart : https://www.youtube.com/watch?v=-CuY5ADwn24
    -   PK - FK - bridge table
    -   1 primary key per entity - unique - never changing - never null
    -   composite primary key : used when two or more attributes are necessary to uniquely indentify every record in the table
        -   this has something to do with relationship

*   numpy > itertuples() > apply()
*   in order to write efficient code, we want to avoid looping when possible
*   random walk : part of probability theory :
    -   https://en.wikipedia.org/wiki/Random_walk : infinite series quite good explain
    -   https://www.youtube.com/watch?v=BfS2H1y6tzQ socratica : good explain with python
*   keyword : plot customization matplotlib

```python
num_list =  [*range(1,12,2)]
from collections import Counter
```

-   how to write clean, fast and efficient python code

*   clean = eliminate loop when possible :
    -   map()
    -   list comprehension
    -   combinations
    -   numpy

-   efficient = reduce latency + overhead
-   how to profile your code for bottlenecks
-   how to eliminate bottlenecks and bad design patterns
-   parallel computing : split task into subtasks -> distribute subtasks over several computers -> work together to finish task
-   cloud : storage - computation - database
-   https://www.w3schools.com/sql/sql_update.asp : update sql
-   https://www.postgresqltutorial.com/psql-commands/ : 17 psql commands
-   sql join -> ERD, relationship, primary/foreign key
-   [database systems cornell university course](database-systems-cornell-university-course)
-   ERD : visual way of looking at your database structure
-   https://www.studytonight.com/dbms/sql-constraints.php : sql constraints
-   sql cook book : reread chapter 3 :join
-   sqlzoo
-   data base vs data warehoues key differeces : https://www.guru99.com/database-vs-data-warehouse.html

```
INNER JOIN table ON condition
```

-   https://www.statisticshowto.com/probability-and-statistics/normal-distributions/ : normal distribution
    -   empirical rule 68-95-99.7 can only be applied to normal distribution
-   https://www.statisticshowto.com/probability-and-statistics/z-score/ : z-score
-   -   quite not true : A low standard deviation means that the data is very closely related to the average, thus very reliable. A high standard deviation means that there is a large variance between the data and the statistical average, and is not as reliable
-   statistical question vs non-statistical question
-   produce report = formalized reporting template
-   ask for a template to do a report
-   DO A PROJECT WITH DATACAMP

```sql
select 'hello world' as result;
```

-   [Datacamp Data Analysis in Excel](Datacamp-Data-Analysis-in-Excel)
-   2 types of seller :
    -   Pro Seller (company/shop/brand)
    -   Private Seller (non company/shop/brand)
-   A contact : buyer Call/SMS/Email/Chat with a Seller
-   https://www.datapine.com/blog/data-analysis-questions/ : **extremly good** must read
-   This table contains the data of contact sellers on all Chotot platforms from 1/1/2016 to 31/3/2016
    1. What are the
        - [x] top 3 regions with highest number of private sellers contacts : tphcm, hanoi, tay nam bo
        - [x] bottom 2 regions with the lowest number of private sellers contacts
            - on desktop platform? And on mobile platforms? (20 points)
    2. What are the top 3 regions that prefer buying from the Pro sellers?
        - [ ] What are the 3 regions that prefer buying from Private Sellers? (25 points)
    3. Please propose
        - the regions for Chotot to focus
        - and the corresponding platform of focus for that region
            - (i.e if you see region A is potential
            - which platform/channel is the most suitable for region A). (25 Points)
    4. Please visualise the provided data
        - in different way to provide
        - [ ] at least 3 findings
            - when comparing private sellers contacts
            - between desktop and mobile platforms. (30 points)

*   https://www.edx.org/course/introduction-to-data-analysis-using-excel-2
    -   What you'll learn
        -   Create flexible data aggregations using pivot tables
        -   Represent data visually using pivot charts
        -   Calculate margins and other common ratios using calculation on pivot table
        -   Filter data using slicers in multiple pivot tables
        -   Create aggregate reports using formula based techniques
*   solve cho tot challenge :
    -   https://www.excel-easy.com/data-analysis.html extremely good resource
    -   https://365datascience.com/trending/chart-types-and-how-to-select-the-right-one/
    -   https://www.optimizesmart.com/how-to-select-best-excel-charts-for-your-data-analysis-reporting/
    -   https://corporatefinanceinstitute.com/resources/excel/study/types-of-graphs/
    -   https://www.optimizesmart.com/how-to-select-best-excel-charts-for-your-data-analysis-reporting/
    -   https://www.youtube.com/watch?v=u4aeZ4ukrqI : how to make pivot table from large dataset
    -   https://databox.com/how-to-analyze-data : MUST READ THIS

-   https://www.youtube.com/watch?v=9yeOJ0ZMUYw
-   [Datacamp Introduction to SQL](Datacamp-Introduction-to-SQL)
-   Datacamp-Data-Analyst
-   [Datacamp Data engineer for everyone](Datacamp-Data-engineer-for-everyone)

-   Software skill vs Analytics skill

-   [Data Warehousing for Business Intelligence](Data-Warehousing-for-Business-Intelligence)

-   probability distribution - average case/ worst case

-   email boilerplate

## middle

```
STRUCTURE : TOP - QUICK NOTE, MIDDLE - IMPORTANT NOTE, BOTTOM - ORGANIZED NOTE
WP:start
logic is reasonable
endgoal of any subject study : STUDY THROUGH BOOK ONLY : encapsulation -> best for look back
GOT REJECTED BY MINDX - 8/4
BEOFRE LEARN ANY NEW SUBJECT, QUORA FOR 'HOW TO STUDY THAT SUBJECT'
QUORA IS BEST ROADMAP
ALWAYS ASK WHAT WAS THE BAD PART THAT I DID
NOT THE KNOWLEDGE BUT HOW TO NAVIGATE TO KNOWLEDGE
```

1. **USE IT OR LOSE IT** :D -> forget everything after understand it
2. RULE OF 3 : ANYTHING CAN BE COMPOSED OF 3 OR LESS ELEMENTS
3. the first thing when you start learning a new subject : learn new vocabulary, key terms
4. meaning of words - different based on **context**
5. communication : MO THAN KET + paraphrase
6. **find structure for everything** - communication **structure** :
    1. problem -> solution -> benefits
    2. what? -> so what? -> now what?
    3. issue -> illustration -> invitation
7. 2 approaches : bottom-up - top-down (page 13 - mathematics for machine learning)(should combine this)
8. classification tree - how to navigate to the knowledge > knowledge
9. code should be the last thing to be paid attention, focus on the process, ideas
10. level of complexity -> if low, skip, high, pay attention and focus the math concept
11. KEYWORD : FUNDAMENTAL THEOREM OF ... | BIG IDEAS OF ... | ... CHEATSHEET | ... CALCULATOR | ... NOTATION | ... COOKBOOK | ... BOILERPLATE/IMPLEMENTAION
12. [I find that learning node.js is difficult for me. Can someone give me an advice?](https://www.quora.com/I-find-that-learning-node-js-is-difficult-for-me-Can-someone-give-me-an-advice)
    - do similar search
13. LEARN TO ASK **BETTER QUESTION** :
    - GOOGLE/**WIKI** HOW TO LEARN ABOUT SOMETHING FIRST RATHER THAN GOOGLE FOR THE THING ITSELF
        - ex : how to learn statistics, how to learn nodejs,...
    - sometimes think about history of a problem
        - https://blog.risingstack.com/the-history-of-react-js-on-a-timeline/ : react history -> google for similar topics of other technology
14. Both **discovery** and **proof** are integral parts of **problem solving**
15. discrete math -> discrete structure -> modeling problems
16. looping - quantification : \forall \exists
17. abduction - sherlock - 'when you have eliminated the immpossible, whatever remains however improbable must be the truth'
18. don't look at things as they have 2 face, look at them as they have 4 face, reduce the posibility and acquire true knowledge
19. rewrite wiki in project based module - knowledge is encapsulated in project based
20. programming : types are object, functions are morphisms | a -> b -> b | arrow : f = a -> b, id_b = b -> b | id_b after f
21. code only when you already understand the concept

## bottom

-   [BA glossy and terms](BA-glossy-and-terms)
-   [quick thought](quick-thought)
-   [roadmap](roadmap)
-   [MYDOCS](MYDOCS)

-   [Mathematics](Mathematics)
-   [Ideology](Ideology)
-   [Technology](Technology)

-   [Finance & Business](Finance-n-Business)
-   [MYPROJECT](MYPROJECT)

-   [Stephen Wolfram](Stephen-Wolfram)
-   [Elon Musk](Elon-Musk)

-   [Archive](archive)
