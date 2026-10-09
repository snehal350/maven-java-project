# Maven Java Project – Build Lifecycle Exercise

**Author:** Snehal Patange
**Course:** DevOps Mini Project 3 (Apache Maven Lifecycle Guide)

## Aim
To install Java and Apache Maven on an Ubuntu server (AWS EC2), create a Java project using a Maven archetype, and run the Maven build lifecycle: compile, test, package and clean.

## Environment
| Item | Details |
|---|---|
| Server | AWS EC2 (t3.micro), Asia Pacific (Mumbai) |
| OS | Ubuntu 26.04 LTS |
| Java | OpenJDK 25 |
| Maven | Apache Maven 3.9.12 |

## Steps Performed

### 1. Install Java and Maven
```bash
sudo apt update
sudo apt install default-jdk -y
sudo apt install maven -y
java -version
mvn -version
```

### 2. Create the Maven project
```bash
mvn archetype:generate -DgroupId=com.careertiq.app -DartifactId=maven-java-project -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
cd maven-java-project
```

### 3. Project structure
```
maven-java-project/
├── pom.xml                 # Project Object Model (config + dependencies)
└── src/
    ├── main/java/...       # Application source code (App.java)
    └── test/java/...       # Unit tests (AppTest.java)
```

### 4. Maven lifecycle commands
```bash
mvn validate
mvn compile
mvn test-compile
mvn test
mvn package
```

### 5. Run the application
```bash
java -cp target/maven-java-project-1.0-SNAPSHOT.jar com.careertiq.app.App
```
**Output:** `Hello World!`

### 6. Clean the build
```bash
mvn clean
```

## Lifecycle Summary
| Command | What it does | Result |
|---|---|---|
| `mvn validate` | Checks the project is correct | No files created |
| `mvn compile` | Converts `.java` to `.class` | `target/classes/` |
| `mvn test-compile` | Compiles the test code | `target/test-classes/` |
| `mvn test` | Runs the unit tests | `target/surefire-reports/` |
| `mvn package` | Bundles the code into a JAR | `target/maven-java-project-1.0-SNAPSHOT.jar` |
| `mvn clean` | Deletes old build output | `target/` folder removed |

## Screenshots
Screenshots of each step are in the `screenshots/` folder.

## Pushing to GitHub
```bash
git init
git add .
git commit -m "Add Maven quickstart project"
git branch -M main
git remote add origin https://github.com/snehal350/maven-java-project.git
git push -u origin main
```

## Conclusion
Maven was installed on an Ubuntu EC2 server, a Java project was generated, and the full build lifecycle (compile, test, package, clean) was run successfully. The packaged JAR ran and printed `Hello World!`.
