# Demo Java Spring Boot REST

<img src="README.png" alt="Spring logo" style="width: 100%;"/>

See http://projects.spring.io/spring-boot/

From the Spring website: "Spring Boot makes it easy to create stand-alone, production-grade Spring based Applications that you can "just run". We take an opinionated view of the Spring platform and third-party libraries so you can get started with minimum fuss. Most Spring Boot applications need very little Spring configuration."

## To create this demo

Verify you have Java 1.7 or better:

    $ java -version
    java version "1.8.0_72"

Verify you have Gradle 2.14 or better:

    $ gradle -version
    Gradle 2.14

Generate a project:

  * Go to http://start.spring.io/
  * Type "com.example.foo" and "demo".
  * Select "Gradle" (not "Maven").
  * Choose "Web" then "SpringMVC".
  * Download the zip file.
  * Unzip it.

Build:

    $ ./gradlew build

Run:

    $ java -jar build/libs/demo-0.0.1-SNAPSHOT.jar

Browse:

    http://localhost:8080

You should see a web page that says "Hello World".

## Extras

This demo also adds:

  * A unit test.
  * An integration test.
  * Actuator, which provides health check monitoring.

## To change ports

There are several ways to change the port number.

Using a Java command line option:

    $ java -Dserver.port=9999 -jar build/libs/demo-0.0.1-SNAPSHOT.jar

Using an environment variable:

    $ SERVER_PORT=9999 java -jar build/libs/demo-0.0.1-SNAPSHOT.jar

Using the file `application.properties` in `src/main/resources/`:

    server.port=9999

Using the file `application.properties` with a custom command line variable:

    server.port=${myport:8080}

    $ java -Dmyport=9999 -jar build/libs/demo-0.0.1-SNAPSHOT.jar

Using the file application.yml:

    server.port: 9999

Using source code:

    @Controller
    public class ServletConfig {
        @Bean
        public EmbeddedServletContainerCustomizer containerCustomizer() {
            return (container -> {
                container.setPort(9999);
            });
        }
    }

Using a scan for a free port, and using OS natives to prevent clashes: use port 0.

To switch off the HTTP endpoints completely, but still create a WebApplicationContext, use port 1. This is sometimes useful for testing.
