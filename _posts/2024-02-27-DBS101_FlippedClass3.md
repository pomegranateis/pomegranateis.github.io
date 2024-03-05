---
Title: DBS101 Flipped Class 3
categories: [DBS101, Flipped_Class1]
tags: [DBS101]
---

# Topic : Null Values and Set Operations in SQL

---

![Desktop View](/home/pomegranateu/DBS101/pomegranateis.github.io){: width="700" height="400" }

## What I did
We started our week with a new lesson learning in depth about DBMS and RDBMS. After that we began learning about SQL starting from its basic structures. Since we only had a few ideas as SQL was still kind of new to us, our tutor assigned us two topics we could discuss on. Set operations and Null values.

Following the same routine as before, our team got assigned Set Operations to learn on. We took turns explaining what each of us understood. It helped us learn a lot from each other although we did refer the same notes. And as usual we switched teams and then explained again to our new friends who got the other topic. It was a fun session, as always. Very interactive and efficient to remember lessons better.

## What I learned
Following will be a brief introduction to basics of both set operations and null values.

### Set Operations

![Desktop View](/home/pomegranateu/Screenshots){: width="700" height="400" }

The SQL Set operation is used to combine two or more SQL SELECT statements.

#### Types of Set Operation
- Union
- UnionAll
- Intersect
- Minus

There are certain rules which must be followed to perform operations using SET operators in SQL. Rules are as follows:

1. The number and order of columns must be the same.
2. Data types must be compatible

#### 1. UNION
The union operation eliminates the duplicate rows from its result set.

##### Syntax

###### SELECT column_name FROM table1  
###### UNION  
###### SELECT column_name FROM table2;  

#### 2. UNION ALL
Union All operation is equal to the Union operation. It returns the set without removing duplication and sorting the data.

##### Syntax:

###### SELECT column_name FROM table1  
###### UNION ALL  
###### SELECT column_name FROM table2; 

#### 3. INTERSECT
This result set has no duplicates and it arranges the data in ascending order by default.

##### Syntax

###### SELECT column_name FROM table1  
###### INTERSECT  
###### SELECT column_name FROM table2; 

#### 4. Minus
It combines the result of two SELECT statements. Minus operator is used to display the rows which are present in the first query but absent in the second query.

It has no duplicates and data arranged in ascending order by default.

##### Syntax:

###### SELECT column_name FROM table1  
###### MINUS  
###### SELECT column_name FROM table2;

### Null Values

A field with a NULL value is a field with no value.

If a field in a table is optional, it is possible to insert a new record or update a record without adding a value to this field. Then, the field will be saved with a NULL value.

##### Note: A NULL value is different from a zero value or a field that contains spaces. A field with a NULL value is one that has been left blank during record creation!

#### How to Test for NULL Values?
It is not possible to test for NULL values with comparison operators, such as =, <, or <>.

We have to use 
- IS NULL and 
- IS NOT NULL 

#### IS NULL Syntax
###### SELECT column_names
###### FROM table_name
###### WHERE column_name IS NULL;

#### IS NOT NULL Syntax
###### SELECT column_names
###### FROM table_name
###### WHERE column_name IS NOT NULL;