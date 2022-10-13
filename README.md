# Spring Boot Session Management


In this tutorial of Spring Boot Session Management will see how to manage session in Spring Boot.

HTTP is a stateless protocol, and to track the activities of request response will need to have session.
Session Management is done by storing session information by Web container...

# Technology

* Java 1.8
* Spring Boot 2.7.3 (with Spring Web MVC, sspring-boot-starter-jdbc, spring-boot-starter-thymeleaf and spring-session-core dependencies)
* Maven 3.8.1 or above

# Create & Setup Spring Boot project
Use Spring web tool or your development tool (Spring Intializer.io, Spring Tool Suite, Eclipse, Intellij) to create a Spring Boot project.

Then open pom.xml and add these dependencies:


* spring-boot-starter-web
* spring-session-core
* spring-boot-starter-jdbc
* spring-boot-starter-thymeleaf
* spring-session-core
* spring-session-jdbc
* mysql-connector-java
* spring-boot-maven-plugin

# Configure Spring boot with MySql  
Under src/main/resources folder, open application.properties.<br />
Add below configuration properties in application.properties
<br />
<br/>
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver <br />
spring.datasource.url=jdbc:mysql://localhost:3306/springBootSession?createDatabaseIfNotExist=true&useSSL=false <br />
spring.datasource.username=root <br />
spring.datasource.password=root <br />
spring.session.store-type=jdbc <br />
spring.session.jdbc.initialize-schema=always <br />
spring.session.timeout.seconds=600 <br />
spring.h2.console.enabled=true <br />

# Run Spring Boot application

mvn spring-boot:run or   <br />
SpringApplication.run(SpringBootSessionManagementApplication.class, args)

# Result

Test this application by the below steps -

* Run SpringBootSessionManagementApplication.java and go to home page <br />
http://localhost:8080/home.

* Enter Note in Textarea and click on Add Note Button to add note in session 
* Go to home page, Note has been added to the session.
* Add second Note in the session.
* Now if you go to the database and see that the 2 tables will be created and the NOTE SESSION object will be stored in this table to manage the session.
* 1. spring_session table and <br/>
  2. spring_session_attributes check the tables entries are their
* Click on Destroy Session, Spring Boot will delete data (NOTES_SESSION) from spring_session_attributes table.
* Now go to home page, session data got cleaned.


