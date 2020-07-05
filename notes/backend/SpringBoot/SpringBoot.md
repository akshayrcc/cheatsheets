# Spring Boot

## Table of Contents

   * [Introduction](#Introduction)
   * [Spring Boot Advantages](#Spring-Boot-Advantages)
   * [Spring Boot Starters](#Spring-Boot-Starters)

## Introduction:

* Spring boot is a spring framework module which simplifies the use of Spring for Java dev.
* Used to create stand alone Spring-based applications easy to run.
* Aims RAD - Rapid Application Developement.
* Instead lot of libraries uses annotations.

## Spring Boot Advantages:
1. Auto dependecy resolution.
2. Auto configurations.
3. Embedded HTTP servers like Tomcat and servlet containers jetty.(to avoid the use of WAR files.)
4. Management Endpoints.
5. Spring boot CLI. (develope and test the app.) (Uses groovy)
6. Opiniated view.
7. Spring boot starters aggregates common dependecies together and improves the productivity -RAD. (org.springframework.boot).
8. Wide range of APIs for monitoring and managing the app.
9. Spring Initializer.
10. Easy integration with Spring eco-system like Spring JDBC, Spring ORM, Spring Data, Spring Security etc.
11. Logging and security.


## Create New Spring Boot app:
1. Spring-Boot CLI
2. Spring-Boot Project Wizard.
3. Spring-Boot Initializer.
4. Spring Maven Project. 

## External Configuration:
1.  Application Properties.
2. Command Line Properties.
3. Profile specific Properties.

## Spring Boot Starters.(org.springframework.boot).
1. spring-boot-starter.
	a. Logging
	b. auto configurations.
	c. YML files
2. spring-boot-starter-jdbc.
	a. hierarchy CP connection pool with JDBC.
3. spring-boot-starter-web.
	a. RESTful web apps using Spring MVC.
4. spring-boot-starter-data-jpa.
	a. use data-jpa with Hibernate.
5. spring-boot-starter-security.
6. spring-boot-starter-aop.
	a. aspect J and Spring AOP
7. spring-boot-starter-test.
8. spring-boot-starter-thymeleaf.
	a. server side template engine.


### Spring Actuator
* Helps to see whats happening inside running application like identifying beans, CPU usage.
* easy way to access Production ready REST endpoints 

### Embedded Tomcat server Port.
 application.properties
	`server.port=8082`
	
### Enable HTTP2 support
`server.http2.enabled=true`

## JPA vs Hibernate
* JPA is a Data Access Abstraction used to reduce the amount of boilerplate code.
* Hibernate is an implementation of Java Persistence API and offers benefits of loose coupling.

@Endpoint
@WebEndpointExtension

* To disable Auto Configuration
@EnableAutoConfiguration(exclude={DataSourceAutoConfiguration.class})

spring.autoconfigure.exclude

* @SpringBootApplication = Used in main class  (@Configuration + @CompenentScan + @EnableAutoConfiguration)

* @EnableAutoConfiguration = @Configuration + @CompenentScan

* Using Spring boot maven plugin we can make a jar/war file for our spring project.
* mention JAR or WAR in the packaging tag.

## Spring Data REST
* used to expose the RESTful resources around the Spring Data Repositories.