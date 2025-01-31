## Building a REST API with Spring Boot

### Introduction

Spring Boot is a powerful framework for building web applications. It simplifies the development process by providing a set of pre-configured beans that handle common tasks such as dependency management, database configuration, and web server configuration.

In this guide, we will create a simple REST API using Spring Boot. We will cover the following steps:

- Setting up the development environment
- Creating the project structure
- Writing the necessary code
- Running the project
- Testing the application
- Adding code to repository and pushing to remote

### Prerequisites

- Java 8 or later
- Maven or Gradle
- Git

### Setting up the Development Environment

1. Install Java 8 or later.
2. Install Maven or Gradle.
3. Install Git.

### Creating the Project Structure

1. Open a terminal window and create a new directory for your project:

```
mkdir spring-boot-api
cd spring-boot-api
```

2. Initialize a Maven project:

```
mvn archetype:generate -DgroupId=com.example -DartifactId=spring-boot-api -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4.1.RELEASE
```

### Writing the Necessary Code

1. Open the `pom.xml` file and add the following dependencies:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>

<dependency>
    <groupId>com.h2database</groupId>
    <artifactId>h2</artifactId>
    <scope>test</scope>
</dependency>

<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```

2. Create a new Java class called `DemoController` in the `src/main/java/com/example/springbootapi` package:

```java
package com.example.springbootapi;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class DemoController {

    @GetMapping("/")
    public String hello() {
        return "Hello, Spring Boot!";
    }

}
```

### Running the Project

1. Run the following command to start the Spring Boot application:

```
mvn spring-boot:run
```

2. Open a web browser and navigate to `http://localhost:8080`. You should see the message "Hello, Spring Boot!".

### Testing the Application

1. Create a new Java class called `DemoControllerTests` in the `src/test/java/com/example/springbootapi` package:

```java
package com.example.springbootapi;

import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;
import org.springframework.test.web.servlet.MockMvc;
import org.springframework.test.web.servlet.request.MockMvcRequestBuilders;
import org.springframework.test.web.servlet.result.MockMvcResultMatchers;
import org.springframework.test.web.servlet.setup.MockMvcBuilders;

@SpringBootTest
public class DemoControllerTests {

    @Autowired
    private DemoController demoController;

    private MockMvc mockMvc;

    @BeforeEach
    public void setup() {
        mockMvc = MockMvcBuilders.standaloneSetup(demoController).build();
    }

    @Test
    public void testHello() throws Exception {
        mockMvc.perform(MockMvcRequestBuilders.get("/"))
                .andExpect(MockMvcResultMatchers.status().isOk())
                .andExpect(MockMvcResultMatchers.content().string("Hello, Spring Boot!"));
    }

}
```

2. Run the following command to run the tests:

```
mvn test
```

### Adding Code to Repository and Pushing to Remote

1. Create a new repository on GitHub or another code hosting platform.
2. Initialize a Git repository in your local project directory:

```
git init
```

3. Add your code to the repository:

```
git add .
```

4. Commit your changes:

```
git commit -m "Initial commit"
```

5. Push your changes to the remote repository:

```
git push origin master
```