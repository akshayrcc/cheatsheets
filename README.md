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
Its a medium between Java Application Layer and Hibernate.
To get session, one can use native HQL queries.
Session provides session object, using which we can perform CRUD operations.

<b>SessionFactory:</b></br>
It's a factory class to get the session object.
SessionFactory is heavy and thread-safe object used by all the threads in the application.

getCurrentSession();
openSession();

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


