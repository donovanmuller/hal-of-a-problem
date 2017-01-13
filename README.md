# Hal of a Problem

A sample Spring Boot app that reproduces the issue
when including the `spring-data-rest-hal-browser` dependency.

Related to this Spring Boot issue: https://github.com/spring-projects/spring-boot/issues/7977

## Issue

When you include `spring-data-rest-hal-browser` 

```xml
    <dependency>
        <groupId>org.springframework.data</groupId>
        <artifactId>spring-data-rest-hal-browser</artifactId>
    </dependency>
```

and attempt to run the app, you will face this issue:

```console
$ mvn spring-boot:run

...

***************************
APPLICATION FAILED TO START
***************************

Description:

Constructor in org.springframework.boot.actuate.autoconfigure.EndpointMBeanExportAutoConfiguration required a single bean, but 3 were found:
    - _halObjectMapper: defined in null
    - objectMapper: defined by method 'objectMapper' in class path resource [org/springframework/data/rest/webmvc/config/RepositoryRestMvcConfiguration.class]
    - halObjectMapper: defined by method 'halObjectMapper' in class path resource [org/springframework/data/rest/webmvc/config/RepositoryRestMvcConfiguration.class]

Action:

Consider marking one of the beans as @Primary, updating the consumer to accept multiple beans, or using @Qualifier to identify the bean that should be consumed
```

## Related issues

There are already some related issues:

### Spring Boot

* https://github.com/spring-projects/spring-boot/issues/6529
* https://github.com/spring-projects/spring-boot/issues/5984
* https://github.com/spring-projects/spring-boot/issues/6517
* https://github.com/spring-projects/spring-boot/issues/5984

### Spring Data REST (probably most relevant)

* https://jira.spring.io/browse/DATAREST-865
