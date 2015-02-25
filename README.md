# springboot-rest-lab
Bootstrap project for the Spring Boot REST tutorial found here: https://spring.io/guides/tutorials/bookmarks/

The tutorial includes four main steps:

* Building the model
* Building a REST service
* Building a HATEOAS REST Service
* Securing a REST Service

Each step is executed in a separate module of the project.

This project contains the four modules (model, rest, hateoas, security) and complete pom.xml files and can be used as
a starting point when following the tutorial.

## Run application
The REST, HATEOAS and security step/module contains an Application class with a main method starting the application.

The application in each step can be started either by running the Application class from your IDE or with Maven. To do
the latter just run the below command in the module which application you want to start:

    mvn spring-boot:run

## Test application with cURL
You can use cURL to test your application at the different steps. Some example commands follows.

### REST/HATEOAS

Get all bookmarks for user jhoeller:

    curl -v GET http://127.0.0.1:8080/jhoeller/bookmarks

### Security

1. Login / get access token for user jhoeller:

        curl -X POST -vu android-bookmarks:123456 http://localhost:8080/oauth/token -H "Accept: application/json" -d "password=password&username=jhoeller&grant_type=password&scope=write&client_secret=123456&client_id=android-bookmarks"

2. Get all bookmarks (for user jhoeller):

        curl -v GET http://127.0.0.1:8080/bookmarks  -H "Authorization: Bearer [access_token from response in above POST request]"

    *(NB! The second example request at the top of the security step Application class in the tutorial is incorrect.)*

## Learn more about Spring Boot
http://projects.spring.io/spring-boot/

http://www.infoq.com/articles/microframeworks1-spring-boot

