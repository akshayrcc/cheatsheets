<!--# <p align="center">Hibernate</p>-->
<p align="center">
  <img width="500" height="120" src="Images/Hibernate.png">
</p>

Table of Contents
-----------------
   * [Introduction](#Introduction)
   * [Advantages](#Advantages)
   * [Supported Functionalities or What Better Over JDBC](#Supported-Functionalities-or-What-Better-Over-JDBC)
   * [Hibernate Overcomes:](#Hibernate-Overcomes)
   * [Techs supported by Hibernate:](#Techs-supported-by-Hibernate)
   * [Hibernate Working:](#Hibernate-Working)
   * [To configure Hibernate:](#To-configure-Hibernate)
   * [Collections in Hibernate](#Collections-in-Hibernate)
   * [Design Patterns Used in Hibernate](#Design-Patterns-Used-in-Hibernate)
   * [Hibernate Tuning](#Hibernate-Tuning)
   * [Important things in Hibernate](#Important-things-in-Hibernate)
   * [Some important methods in Hibernate](#Some-important-methods-in-Hibernate)
   * [Cache in Hibernate](#Cache-in-Hibernate)
   * [Best Practices for Persistent Classes in Hibernate](#Best-Practices-for-Persistent-Classes-in-Hibernate)
   
   
Introduction
------------
- Hibernate is a Java Framework made for ORM - Object Relational Mapping.
- ORM tool is a technique that maps the object that is stored in the database.
- An ORM tool helps in simplifying data creation, manipulation and access.

<p align="center"><img width="700" height="150" src="Images/ORM_tool_architecture.jpg"></p>

Advantages
------------
1. Open Source and Light Weight.
2. Best Performance.
3. Helps to generate independent Queries.
4. Provides facilities to create a table.
5. Provides Query Statistics and database status.

Supported Functionalities or What Better Over JDBC
--------------------------------------------------
1. Hibernate eliminates a lot of boiler plate code.
2. Support inheritance, association and collections.
3. Uses HQL which is Object Oriented and close to Java.
4. Implicitly provides transaction Management.
5. Hibernate wrapes JDBC exceptions and only throws the ones which are unchecked.Reducing the usage of try catch blocks as compared to JDBC.So, exception handling is not mandatory.
6. Supports auto DDL opertations, auto primary key generation support.
7. Supports cache memory.

Hibernate Overcomes
--------------------
1. Database dependecy faced in the JDBC.
2. Changing of DB cost a lot in JDBC.
3. Code Portability is eaisily handled.
4. It overcomes exception handling.

Techs supported by Hibernate
-----------------------------
1. Java J2EE.
2. Maven.
3. Eclipse Plugins.
4. X-Doclets.

<p align="center"><img width="450" height="450" src="Images/hbm_jpa.jpg"></p>

Hibernate Working
-----------------
Association mappings is a key feature in Hibernate.
Hibernate supports same associations as relational database model.
viz, One-to-One, Many-to-One, Many-to-Many.
Hibernate Config File: It has database type and class details.

<b>Important Interfaces:</b>
1. Session Factory.
2. Session.
3. Transaction.

<b>Session in Hibernate:</b></br>
Session a medium between Java Application Layer and Hibernate.
To get session, one can use native HQL queries.
Session provides session object, using which we can perform CRUD operations.

<b>SessionFactory:</b></br>
SessionFactory is a factory class to get the session object.
It is heavy and thread-safe object used by all the threads in the application.

getCurrentSession();
openSession();

<b>Hibernate Configuration File:</b></br>
It has database type, connection and class mapping details.

<b>Important Annotations Used:</b></br>
javax.persistence.Entity;
javax.persistence.Table;
javax.persistence.Access;
javax.persistence.Embedded Id;
javax.persistence.Column;
javax.persistence.GeneratedValue;


To configure Hibernate
----------------------
1. Identify the POJOs that has database representation.
2. Identify which properties of POJO to continue.
3. Annote each of these POJOs to map Java Obj to DB column.
4. Create DB schema.
5. Add hibernate Java Liabraries.
6. Create hibernate configuraion XML file. (test.hbm.xml)
7. In Java app, create hibernate configuraion object that refers to XML configuraion file.
8. From hibernate configuraion object, build the SessionFactory object.
9. Then retrieve the hibernate session object from SessionFactory object.
10. Using hibernate session object, we can write access logic as CRUD for the app.

Collections in Hibernate
-------------------------
(One-to-Many Mapping)
Bag
Lists
Sets
Array
Maps
(Other)
Sorted Sets
Sorted Maps
  Hibernate injects these collections based on the type of Interface.


Design Patterns Used in Hibernate
---------------------------------
1. Domain Model pattern.
2. Data mapper.
3. Proxy pattern.
4. Factory pattern.

Hibernate Tuning
----------------
Optimizing the performance of the hibernate application. It includes below:
1. SQL Optimization.
2. Session Manaagement.
3. Data Caching.

Important things in Hibernate
-----------------------------
<b>Transaction Management in Hibernate:</b></br>
1. It's a process of managing a set of commands or statements.
2. A transaction is associated with Session and it is instatiated by calling session.beginTransaction().

<b>States of Persistent Entity:</b></br>
1. <b>Transient:</b> Not associated with session and has no representation in the Database.
2. <b>Persistent:</b> Transient instance made as persistent by associating it with a session.
3. <b>Detached:</b> If we close the Hibernate session the Persistent instance will become Detached instance of the class.

<b>Hibernate Proxy - Lazy Loading:</b></br>
1. Hibernate uses proxy object to support Lazy loading.
2. Hibernate doesn't load all the mapped objects.
3. After you reference a child object through getter methods, then the proxy code will be entered to the database.
4. It uses java assist to effectively and dynamically generate sub-classed implementations.

<b>Named SQL query in Hibernate:</b></br>
1. We can define names SQL query in hibernate and use them anywhere in the code.n
2. To define native SQL queries in hibernate mappings file we can use below tags:
@NamedQuery
@NamedNativeQuery.

<b>SortedCollection:</b> It sorts data in JVMs heap memory using Java's collection framework sorting methods. It's suitable for small dataset.
<b>OrderedCollection:</b> It sorts data using 'order by clause' in database.

<b>Light Object Mapping:</b></br>
It means syntax is hidden from the busineess logic using specific design patterns.

<b>Template class</b></br>
1. Automated session closing.
2. Hibernate session interaction is easy.
3. Exception handling is automated.

Some important methods in Hibernate
-----------------------------------
<b>Merge():</b> Merging modifications anytime without considering the state of the session.
<b>Update():</b> When hibernate session does not contain an already persistent instance with the same id.

<b>Load():</b> Throws exception when object with given id not found. It can return proxy without hitting the database unless required.
<b>Get():</b>  Returns null when object with given id not found. It'll always goes to database.

<b>save():</b> Only insert records.
<b>saveOrUpdate():</b> insert and update records.

Cache in Hibernate
------------------
First Level Cache: It's maintained at the Session Level.
Second Level Cache: It's maintained at the session factory level and is shared by all sessions.

<b>Query cache in Hibernate:</b></br>
1. Separate cache region for Query Resultset that integrates with the Hibernate second-level cache.
2. Useful only when query uses the same parameters.

Best Practices for Persistent Classes in Hibernate
--------------------------------------------------
1. Java classes should have default constructor.
2. Classes should contain a ID.
3. Attributes should be declared private.
4. Always check primary key field access.
5. Use native SQL query only when it's not possible using HQL.
6. Use named queries wisely and keep them at a single place to ease the debugging.
7. Avoid many to many relationship by using bi-directional one-to-many and many-to-one relationships.
8. For collections, for the benefit of lazy loading, try to use Lists, Maps and Sets. Avoid arrays.
9. Prefer DAO pattern, for exposing the different methods that can be used 	with entity beans.
10. For Web Application, try to use JNDI DataSource rather than configuring to create a connection in hibernate.
