## Building a REST API using Spring Boot

### Setting Up the Development Environment

- Install Java Development Kit (JDK) 17 or higher.
- Install Maven 3.8 or higher.
- Install an IDE like IntelliJ IDEA, Visual Studio Code, or Eclipse.

### Creating the Project Structure

- Open your IDE and create a new Maven project.
- In the "GroupId" field, enter the reverse domain name of your organization (e.g., com.example).
- In the "ArtifactId" field, enter a unique name for your project (e.g., spring-boot-rest-api).
- Select "Java" as the programming language and "Maven" as the build tool.

### Writing the Necessary Code

**pom.xml**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>spring-boot-rest-api</artifactId>
    <version>0.0.1-SNAPSHOT</version>

    <properties>
        <java.version>17</java.version>
        <spring-boot.version>3.0.1</spring-boot.version>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
            <version>${spring-boot.version}</version>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <version>${spring-boot.version}</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <version>${spring-boot.version}</version>
            </plugin>
        </plugins>
    </build>

</project>
```

**Application.java**

```java
package com.example;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@SpringBootApplication
@RestController
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }

    @GetMapping("/")
    public String hello() {
        return "Hello, world!";
    }
}
```

### Running the Project

- In your IDE, right-click on the project and select "Run 'Application'".
- The application will start running on port 8080 by default.

### Testing the Application

- Open a terminal window and run the following command:

```
curl http://localhost:8080
```

- You should see the response "Hello, world!" in the terminal.

### Adding Code to Repository and Pushing to Remote

- Open a terminal window and navigate to the project directory.
- Initialize a new Git repository:

```
git init
```

- Add the project files to the staging area:

```
git add .
```

- Commit the changes:

```
git commit -m "Initial commit"
```

- Create a remote repository on GitHub or any other platform.
- Add the remote repository to your local repository:

```
git remote add origin <remote_repository_url>
```

- Push the changes to the remote repository:

```
git push origin main
```

### Conclusion

You have now successfully built and tested a simple REST API using Spring Boot. You have also added the code to a remote repository for version control and collaboration.