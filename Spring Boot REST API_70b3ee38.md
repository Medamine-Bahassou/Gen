## Building a REST API Using Spring Boot: A Comprehensive Guide for Beginners

### Introduction

In this tutorial, we will guide you through the process of building a simple REST API using Spring Boot, a powerful Java framework for developing modern web applications.

### Setting Up the Development Environment

1. Install Java Development Kit (JDK) version 11 or later.
2. Install a code editor or IDE, such as IntelliJ IDEA, Visual Studio Code, or Eclipse.
3. Install Maven, a build automation tool.

### Creating the Project Structure

1. Open a terminal or command prompt.
2. Create a new directory for your project: `mkdir spring-boot-api`
3. Navigate to the project directory: `cd spring-boot-api`
4. Initialize a new Maven project using the Spring Boot CLI: `mvn archetype:generate -DarchetypeArtifactId=spring-boot-starter-parent -DarchetypeGroupId=org.springframework.boot -DarchetypeVersion=2.7.3`

### Writing the Necessary Code

1. Open the generated `pom.xml` file in your code editor.
2. Add the following dependency to enable Spring Web:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

3. Create a new Java class named `MessageController.java` in the `src/main/java` directory. This class will handle HTTP requests:

```java
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api")
public class MessageController {

    @GetMapping("/message")
    public String getMessage() {
        return "Hello, World!";
    }
}
```

### Running the Project

1. Open a terminal or command prompt in the project directory.
2. Run the following command to start the application: `mvn spring-boot:run`

### Testing the Application

1. Open a web browser and navigate to the following URL: `http://localhost:8080/api/message`
2. You should see the message "Hello, World!" displayed in the browser.

### Adding Code to Repository and Pushing to Remote

1. Create a new repository on GitHub or any other code hosting platform.
2. Initialize a local Git repository in your project directory: `git init`
3. Add all files to the staging area: `git add .`
4. Commit the changes: `git commit -m "Initial commit"`
5. Link the local repository to the remote repository: `git remote add origin <repository URL>`
6. Push the changes to the remote repository: `git push -u origin main`

### Conclusion

Congratulations! You have successfully built a simple REST API using Spring Boot. This guide has provided you with a solid foundation for developing more complex and feature-rich web applications. To further enhance your skills, explore additional Spring Boot features and best practices.