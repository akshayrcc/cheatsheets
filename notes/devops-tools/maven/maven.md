# maven

![Image of Apache Maven](img/apache-maven.jpeg)


## Table of Contents

   * [Basic commands](#Basic-commands)
   * [POM.xml](#POM.xml)
   * [Maven tools](#Maven-tools)

## Basic commands:

 * To check maven's version:
	```
	mvn --version
	```
 * Executing maven gaol to create a Project:
 
 ```
 mvn archetype:generate -DgroupId=com.mycompany.app -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
 ```

 * To compile and Package the project code.
	```
	mvn package
	```
## POM.xml
 
 * POM stands for Project Object Model.
 * POM.xml file is project configuration file in the maven. Here, we write all the project dependecies.
 * Sample file:
 ```
     <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
      <modelVersion>4.0.0</modelVersion>
     
      <groupId>com.mycompany.app</groupId>
      <artifactId>my-app</artifactId>
      <version>1.0-SNAPSHOT</version>
     
      <properties>
        <maven.compiler.source>1.7</maven.compiler.source>
        <maven.compiler.target>1.7</maven.compiler.target>
      </properties>
     
      <dependencies>
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-core</artifactId>
			<version>5.2.7.RELEASE</version>
		</dependency>
        <dependency>
          <groupId>junit</groupId>
          <artifactId>junit</artifactId>
          <version>4.12</version>
          <scope>test</scope>
        </dependency>
      </dependencies>
	  
    </project>
 ```
## Maven tools

   * `validate`: To validate the project is correct and all necessary information is available.
   * `compile`: To compile the source code of the project.
   * `test`: To test the compiled source code using a suitable unit testing framework. These tests should not require the code be packaged or deployed.
   * `package`: To take the compiled code and package it in its distributable format, such as a JAR.
   * `integration-test`: To process and deploy the package if necessary into an environment where integration tests can be run.
   * `verify`: To run any checks to verify the package is valid and meets quality criteria.
   * `install`: To install the package into the local repository, for use as a dependency in other projects locally.
   * `deploy`: To be done in an integration or release environment, copies the final package to the remote repository for sharing with other developers and projects.
   * `clean`: To clean up artifacts created by prior builds.
   * `site`: To generate site documentation for this project.



