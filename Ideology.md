# Ideology

-   COMPLEXITY - CLUTTER - STATUS QUO <-- IMPORTANT
    -   [TED - Simplifying complexity](https://www.ted.com/talks/eric_berlow_simplifying_complexity?language=en) - focus on a small part of the grap
    -   [TED - From clutter to clarity - Kerry Thomas](https://www.youtube.com/watch?v=CrsdoIOGCRw) - make decision
    *   [Use this to control your brain - Mel Robins](https://www.youtube.com/watch?v=JRzWRZahOVU)
        -   brain protect you by stopping you from uncertain, new, or scary
        -   decision maker vs autopilot, self doubt -> 5s rule to beat these shit
        -   5, 4, 3, 2, 1, -> **CHANGE STATE**
    -   https://www.youtube.com/watch?v=MrZAGVq25zw
    -   5 principles :
        -   1. internal locus of control
            -   bias toward action(5s rule) vs bias toward thinking
        -   2. behavioral flexibility
        -   3. do good be good
        -   4. the golden rule of habits
            -   you can never change the things that trigger you
            -   you can't control your urges or how you might feel
            -   **-> but you can always choose how you behave**

*   vertical : bigger or smaller (more detail or bigger picture)
*   horizontal : same level
-   search keyword : glossary and terms
    -   https://www.workspace.co.uk/content-hub/entrepreneurs/glossary-of-business-terminology
    -   https://www.batimes.com/business-analyst-glossary-and-terms.html
    -   [145 keys BA concepts that you should know](https://medium.com/techcatch/145-key-business-analysis-concepts-that-you-should-know-e65d1736a964)
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
# https://www.datacamp.com/community/tutorials/usage-asterisks-python
# asterisks - the same as :
num_list =  [i for i in range(1,12,2)]
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

- https://theessentialman.com/business-casual-style-guide-men/ best article about outfit
    - read this only 1 link

- https://www.youtube.com/watch?v=k-J9BVBjK3o : 20 sign you're emotionally mature
- [the magical science of storytelling](https://www.youtube.com/watch?v=Nj-hdQMa3uA)
-   [ ] [science](science) of ideas - belief - philosophy - epistemic
    -   [ ] to develop a rational system of ideas to oppose the irrational impulses - group decisions

# Toolbox

-   black box (remember) - reasoning (connecting) => 50% understanding
-   abstraction - reverse engineering
-   buy - sell, problem - solution
-   tool for dealing with email things : grammarly, languagetool
-   Any company that provide technology solution they all have kind of training :

    -   microsoft training, wolfram U, mysql,...
    -   vsbenefits-wolfram
    -   business - solution

-   [craft.co top competitors - owler](https://www.owler.com/company/craft)
    -   wolfram alpha
    -   thomson reuters
    -   dun & bradstreet
    -   owler
    -   craft.co

# Lessons

-   [how to spot liars at work](https://www.youtube.com/watch?v=oywoZQ5_zd8)
-   [make body language your superpower](https://www.youtube.com/watch?v=cFLjudWTuGQ)
-   [nhan tuong hoc trong nhan su](https://www.youtube.com/watch?v=avGhBfvIGwY)
-   Huynh Duy Khuong
    -   [3 cach su dung ngon ngu co the thu hut nguoi nghe](https://www.youtube.com/watch?v=xPY9EHVp_1E)
    -   [bi quyet de co giong noi thu hut](https://www.youtube.com/watch?v=GRiQ80T9RZI)
        1. toc do
        2. cuong do
        3. truong do : noi chuyen la phai dut khoat
        4. cao do
        5. am sac
    -   [5 sai lam trong giao tiep](https://www.youtube.com/watch?v=AP-_aTAUNRs)
        -   ko dc mac dinh cai tu trong dau nguoi ta cung giong cai tu trong dau cua minh
        1. khong ap a ap ung
        2. khong co gi de coi : ngon ngu co the
        3. noi chuyen vong vo : MO THAN KET
        4. noi chuyen chung chung, ko chi tiet
        5. noi dieu minh muon noi chu khong noi dieu nguoi ta muon nghe : no co lien quan gi den cuoc doi cua toi
    -   SU DUNG NHUNG CAI NAY DE LAM BAI THUYET TRINH MINDX
-   [introduction to business analytics](introduction-to-business-analytics)
-   [think fast talk smart communication techniques](think-fast-talk-smart-communication-techniques)
-   [the counterintuitive way to be more persuasive](the-counterintuitive-way-to-be-more-persuasive)
-   [khan academy navigate your career](khan-academy-navigate-your-career)
-   [crash course linguistics](crash-course-linguistics)
-   [geography](geography)
-   [should knowledge be free](should-knowledge-be-free)
-   [how to become a straight A student](how-to-become-a-straight-A-student)
-   [imagination its not what you think its how you think](imagination-its-not-what-you-think-its-how-you-think)
    -   stop label people or yourself
    -   this is hard -> no it's not
-   [Art](Art)
-   [crash course world history](crash-course-world-history)
-   [crash course big history](crash-course-big-history) : need chemistry, a bit of physics
-   [PMBOK-projectmanagement](PM-simplified-PMIframework-fundamentals)
-   fake it til you make it : powerpose
-   [how to stay calm when you know you'll be stressed](https://www.youtube.com/watch?v=8jPQjjsBbIc) : => when stressed, put system in place, prepare for the moment
-   [crash course philosophy](crash-course-philosophy)
-   [crash course economics](crash-course-economics)
-   [crash course business](crash-course-business)
-   [crash course entrepreneurship](crash-course-entrepreneurship)
-   [research skills](research skills)
-   https://en.wikipedia.org/wiki/Enterprise_life_cycle
-   [How to Read a Book a Day](How-to-Read-a-Book-a-Day)
-   [TED - The single biggest reason why start-ups succeed - Bill Gross](reason-startup-succeed-bill-gross)
-   [how to master emotions](https://www.youtube.com/watch?v=QGQQ7pJQqHk) : different viewpoint => different emotions

# Self remind notes

```important
To prevent relapse
you have to plan for what happens if you ever failed
to control your behavior
```

-   concise
-   control emotion
-   respect
-   always think first => close your eyes, breath deeply
-   be honest
-   cooperative
-   problem-driven
-   Pay attention to your tone of voice, facial expression and gestures
-   do not show off, when communicating, listen, then ask question which is relevant for a specific purpose

    -   do not ask just for show off
    -   da banh - talked to huy ngo, repeat big O

-   [ ] **ALWAYS**, **ALWAYS** ASK , WHAT IT MEANS TO **"LEARN BY YOURSELF"**? : oh my fucking god, i just answered this question! Sat Dec 19 07:34:27 PM +07 2020
    -   [ ] **First-principles** thinking is one of the best ways to **reverse-engineer** complicated problems and unleash creative possibility
    -   [ ] Reasoning by first principles removes the impurity of assumptions and conventions
    -   [ ] element, base, basic, basis
    -   [ ] https://www.valueinspiration.com/incremental-or-exponential-thinking-down-and-dirty-on-the-gamechanging-shift/ incremental vs exponential thinking
