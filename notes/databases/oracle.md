# Oracle - SQL : Sequential Query Language
* RDBMS

## SQL Clauses:

1. where: 

2. group by: aggregate functions like sum(), avg().

3. having:

4. order by: having is filter on aggregate functions.

## Where clause pattern matching:

* Like : sf where col_1 like "%nasty%";

* NOT: 

* Specific position ( underscore): col_1 like "__baba%";

## Subquery:

* Nested statement: 
1. Correlated: (Subquery that is dependent on the main query).
2. Non Correlated: Independent query.

## Joins:
1. Inner Join:
	Select * from table A JOIN table B.
	
2. Left Join:
	All rows from left and corresponding right or null.
	
3. Right Join:
	
4. Full Join:
	Select everything and fill corresponding left / right with NULL if no match.

5. Cross Join:
	A X B = (A cross B) cartesion product.
	
## Indexing:
	
* DS(BTree, B+Tress) that provides quick lookup based upon queries in a column or set of columns.
	
	create index 'stud_score_indx' ON students(id,score);
 
 1. * Unique Index: Data integrity and constant check.
 
	* Non-Unique Index: Speed up more.
 
 2. * Clustered Index: Change the way data is stored in the DB as per the index.
	* On a table, only one CI can be there.
	* It changes the order of the rows.
	* faster performance.
 
	* Non Clustered Index:  Maintain separate DS to optimize the query.
	* Can be many non-CI.	
 
 
## Views:
	Readable copy.


## DBMS Types:
1. OLTP:
	* Many queries
	* Small queries
	* Distributed
	* Faster
	
2. OLAP:
	* Few queries
	* Large queries
	* Analytical Data
	* Large data processing.
	

## Normalization:

* Good DB design.
* arranging E-R.
* reduce data redendency.

1. 1NF: Remove column which has more then 1 value.

2. 2NF: Any set of column which can be identified uniquely other than primary key, make it separate table.



## Aggregate Functions:
* AVG(), SUM(), MIN(), MAX(), FIRST(), LAST()
* used with having / group by.

## Scalar functions:
* Take one value and return one value.
* UCASE() , LCASE(), CONCAT(), RAND(), ROUND(), To_timestamp(), NOW().

## Primary/ Foreign / Candidate Key constraints:
* Unique, not null, default, foreign key, check