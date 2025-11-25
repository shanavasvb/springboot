# 📚 Spring Boot Final Exam Study Guide

A comprehensive study plan based on official lecture notes covering Spring Boot fundamentals, REST APIs, JPA, Security, and deployment.

---

## 📖 Table of Contents

- [Unit 1: Spring Boot Core + Beans + Build Tool](#unit-1-spring-boot-core--beans--build-tool)
- [Unit 2: REST API + Exception Handling](#unit-2-rest-api--exception-handling)
- [Unit 3: Spring Data JPA](#unit-3-spring-data-jpa)
- [Unit 4: Spring Security + JWT](#unit-4-spring-security--jwt)
- [Unit 5: Actuator + Deployment + Profiles](#unit-5-actuator--deployment--profiles)
- [Revision Strategy](#revision-strategy)
- [Understanding Spring Beans](#understanding-spring-beans)

---

## 📍 Unit 1: Spring Boot Core + Beans + Build Tool

### 🎯 Must Cover Concepts

- **Spring Beans, IoC, Dependency Injection** (Constructor, Setter, Field Injection)
- **@SpringBootApplication, Auto Configuration, Component Scan**
- **Build Tools (Maven)**: compile, dependency management, packaging
- **Layered Architecture**: Controller, Service, Repository, Entity

### 📝 Expected Questions

- Define Beans and different ways to create them (PYQ + Internal)
- Explain Build Tool (Maven) with advantages
- Explain @SpringBootApplication roles

### 📚 Detailed Topics Covered

- [Spring Beans](#understanding-spring-beans)
- [IoC (Inversion of Control)](#ioc-inversion-of-control)
- [Dependency Injection](#dependency-injection-di)
- [Types of Dependency Injection](#types-of-dependency-injection)
- [@SpringBootApplication & Auto-Configuration](#springbootapplication--auto-configuration)
- [Ways to Create Spring Beans](#ways-to-create-spring-beans)
- [Layered Architecture](#layered-architecture-in-spring-boot)
- [Maven Build Tool](#maven-build-tool)

---

## 📍 Unit 2: REST API + Exception Handling

### 🎯 Must Cover Concepts

- **REST vs SOAP**, URL, Endpoints
- **Handler Methods**: @GetMapping, @PostMapping, @PutMapping, @DeleteMapping
- **Input Parameters**: @PathVariable, @RequestBody
- **Global Exception Handling**: @ControllerAdvice + @ExceptionHandler + Custom Model
- **Error Response Model**: Standard error JSON format

### 📝 Expected Questions

- What is @RequestBody/@PathVariable?
- Explain Handler Methods with example
- Implement global exception handling (PYQ)

### 🔥 Priority Topics (Based on PYQ + Internal)

| Priority | Topic |
|----------|-------|
| ⭐⭐⭐⭐⭐ | REST Controller + Handler Methods |
| ⭐⭐⭐⭐⭐ | `@PathVariable` + `@RequestBody` |
| ⭐⭐⭐⭐⭐ | Global Exception Handling (`@ControllerAdvice`) |
| ⭐⭐⭐⭐ | Custom Exception |
| ⭐⭐⭐ | Error Response JSON Model |
| ⭐⭐ | ResponseEntity |
| ⭐ | Validation |

### 📚 Detailed Topics Covered

- [REST Controller & Handler Methods](#rest-controller--handler-methods)
- [@PathVariable and @RequestBody](#pathvariable-and-requestbody)
- [Exception Handling in REST](#exception-handling-in-rest)

---

## 📍 Unit 3: Spring Data JPA

### 🎯 Must Cover Concepts

- **ORM, JPA, Hibernate**
- **Entity + JPA Annotations**: @Entity, @Id, @Table
- **Repository**: JpaRepository, CRUD methods
- **Query Methods + @Query** (JPQL & Native)

### 📝 Expected Questions

- Explain JPA annotations used to map objects (PYQ)
- Explain JpaRepository (Internal)
- Query Methods vs @Query with example (Internal + PYQ)

### 📚 Detailed Topics Covered

- [JPA Entity and Annotations](#jpa-entity-and-annotations)
- [CRUD Operations with JpaRepository](#crud-operations-with-jparepository)
- [Query Methods](#query-methods-in-jpa)
- [Custom JPQL and Native Queries](#custom-jpql-and-native-sql-queries)
- [JPA Relationships](#jpa-relationships)

---

## 📍 Unit 4: Spring Security + JWT

### 🎯 Must Cover Concepts

- **Authentication vs Authorization**
- **SecurityFilterChain** (REPLACEMENT of WebSecurityConfigurerAdapter)
- **In-memory Authentication + Role-Based Security**
- **Token Based Authentication + JWT Components**

### 🚨 Study JWT Components in Detail

1. JWT Token Provider
2. Authentication Filter
3. Authentication Manager
4. UserDetailsService
5. Authentication Controller
6. Auth Request + Response DTO

### 📝 Expected Questions

- Explain Token-Based Authentication (Internal)
- How does JWT work in Spring? (Internal 10-mark)
- Customizing Security Filter Chain (Internal)

---

## 📍 Unit 5: Actuator + Deployment + Profiles

### 🎯 Must Cover Concepts

- **Actuator + endpoints**
- **Spring Profiles**
- **Deployment Steps**, Jar, Docker basics

### 📝 Expected Questions

- What is Actuator? Write endpoints (Internal)
- How to configure Actuator?
- Explain Profiles with example
- Steps to deploy a Spring Boot app (PYQ)

---

## 🏆 Revision Strategy

### Based on Mark Weightage

| Marks Type | Study Style                                      |
|------------|--------------------------------------------------|
| 2.5 Marks  | Only definition + 1 short line + 1 example       |
| 5 Marks    | Small diagram + explanation + small code         |
| 10 Marks   | Step-by-step + full code + diagram + explanation |

---

## 🌱 Understanding Spring Beans

### What is a Spring Bean?

A **Spring Bean** is simply a **normal Java object** (class) that **Spring creates and manages for you**.

Instead of manually writing:

```java
EmployeeService service = new EmployeeService();
```

Spring creates it automatically and provides it when needed.

> **Definition**: A Spring Bean is an object created and managed by the Spring IoC container, instead of being created manually in the application.

### 💡 Why is it useful?

- You don't create objects manually
- You don't manage their lifecycle
- Spring handles everything automatically

⚙️ **Spring manages beans using the IoC container**

### 🎯 Example

```java
@Component
public class EmployeeService {
    // Business logic here
}
```

Here, Spring will automatically create an object of `EmployeeService` — this object is called a **Spring Bean**.

---

## 🔄 IoC (Inversion of Control)

### 🧠 Simple Definition

IoC means we do NOT create or control objects ourselves. Instead, Spring creates and manages objects (beans) for us.

> **Key Concept**: The control of object creation is inverted from the programmer to the Spring IoC Container.

### 🏗️ Real-Life Example

**Without Spring (You control everything)** ❌

```java
EmployeeService service = new EmployeeService();
```

**With Spring IoC (Container controls)** ✔

```java
EmployeeService service = context.getBean(EmployeeService.class);
```

🎉 You don't create objects. You ask Spring for them.

### 🧰 What is an IoC Container?

It is a Spring component that creates, manages, and supplies beans.

📌 **Two main containers:**

| Container | Use |
|-----------|-----|
| `ApplicationContext` | ✔ Used in real Spring Boot apps |
| `BeanFactory` | Basic, rarely used |

### 🧪 IoC with Code Example

**Step 1: Create a Bean using @Component**

```java
import org.springframework.stereotype.Component;

@Component
public class EmployeeDao {
    public String getEmployee() {
        return "Employee Data";
    }
}
```

**Step 2: Ask Spring to Retrieve the Bean (IoC in Action)**

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.ApplicationContext;

@SpringBootApplication
public class MainApp {
    public static void main(String[] args) {
        // IoC Container started 🚀
        ApplicationContext context = SpringApplication.run(MainApp.class, args);
        
        // Getting the bean from container (Not created by new keyword)
        EmployeeDao dao = context.getBean(EmployeeDao.class);
        
        System.out.println(dao.getEmployee());
    }
}
```

📌 Here, we never used `new EmployeeDao()` → IoC Container provided the object.

### 🪢 How It Works Internally

```
         ┌──────────────────────────────┐
         │       IoC Container           │
         │ (ApplicationContext)          │
         └──────────────┬───────────────┘
                        │ Creates
                        │ Manages
                        ▼
              [ Spring Beans (@Component) ]
```

### 📝 Summary Table

| Feature | Without IoC | With IoC |
|---------|-------------|----------|
| Who creates objects? | Programmer | Spring Container |
| Object lifecycle? | Manually controlled | Spring manages |
| Loose Coupling? | ❌ No | ✔ Yes |
| Technique used | `new` keyword | Beans + DI |

### 🏆 Exam-Friendly Answer

> IoC (Inversion of Control) is a Spring concept where the responsibility of creating and managing objects (beans) is transferred from the application code to the Spring IoC Container (ApplicationContext). Instead of using `new`, objects are created and provided by the container, improving loose coupling and program flexibility.

---

## 💡 Dependency Injection (DI)

### 🧠 Simple Definition

Dependency Injection means Spring gives the required object (dependency) to a class automatically. You don't create it using `new`.

📌 The object we need is injected into our class by Spring, not by us.

### 🎯 Why do we need DI?

**Without DI (you create objects yourself)** ❌

```java
EmployeeDao dao = new EmployeeDao();  // you create it manually
```

**With DI (Spring creates & supplies)** ✔

```java
@Autowired
EmployeeDao dao;  // Spring injects it automatically
```

👉 DI reduces manual object creation and makes code loosely coupled.

### 🧪 Example with DI in Spring Boot

**Step 1: Create DAO Class**

```java
import org.springframework.stereotype.Repository;

@Repository
public class EmployeeDao {
    public String getEmployee() {
        return "Employee Data from DAO";
    }
}
```

📌 `@Repository` tells Spring to create a Bean of this class.

**Step 2: Service Class Using DI**

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class EmployeeService {
    
    @Autowired   // Dependency Injection happens here 👇
    private EmployeeDao employeeDao;
    
    public String showEmployee() {
        return employeeDao.getEmployee(); // using injected dependency
    }
}
```

📌 We did NOT use `new EmployeeDao()` — Spring provided it.

**Step 3: Controller Using DI**

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class EmployeeController {
    
    @Autowired
    private EmployeeService employeeService;
    
    @GetMapping("/employee")
    public String getEmp() {
        return employeeService.showEmployee();
    }
}
```

✔ `EmployeeService` is automatically injected into the controller.

### 🔗 DI Flow Diagram

```
[Controller]  --uses-->  [Service]  --uses-->  [DAO]

       🔽 DI                     🔽 DI
 Spring injects           Spring injects
```

👉 Spring injects objects into each other, so they work together automatically.

### 🏆 Exam Answer (Short & Perfect)

> Dependency Injection is a technique in Spring where the IoC Container automatically provides required objects (dependencies) to a class without using `new`. It improves loose coupling and makes Spring manage object creation.

---

## 🔄 Types of Dependency Injection

### 1️⃣ Constructor Injection (Recommended)

✔ Dependency is injected through the class constructor  
✔ Best way to inject required dependencies (mandatory objects)

```java
@Service
public class EmployeeService {
    
    private final EmployeeDao employeeDao;
    
    // Constructor Injection
    public EmployeeService(EmployeeDao employeeDao) {
        this.employeeDao = employeeDao;
    }
}
```

**When to use?**
- When dependency is required/mandatory
- When you want immutability (using `final`)
- Recommended for large & secure systems
- Best for unit testing

### 2️⃣ Setter Injection

✔ Dependency is injected through a public setter method  
✔ Used when dependency is optional or changeable

```java
@Service
public class EmployeeService {
    
    private EmployeeDao employeeDao;
    
    @Autowired
    public void setEmployeeDao(EmployeeDao employeeDao) {
        this.employeeDao = employeeDao;
    }
}
```

**When to use?**
- When dependency can be changed
- When dependency is optional
- Good for testing different objects

### 3️⃣ Field Injection

✔ Dependency is injected directly into the variable (field)

```java
@Service
public class EmployeeService {
    
    @Autowired
    private EmployeeDao employeeDao;
}
```

**When to use?**
- Very small projects
- Quick demos, prototypes
- NOT recommended for real large systems because it makes code hard to test

### 🆚 Comparison Table

| Feature | Constructor Injection | Setter Injection | Field Injection |
|---------|----------------------|------------------|-----------------|
| Injection location | Constructor | Setter method | Variable/field |
| Uses `@Autowired`? | Not needed in recent Spring | Yes | Yes |
| Dependency required? | ✔ Yes, good | Optional | Optional |
| Recommended? | 👍 Most Recommended | 👍 Good | 👎 Not recommended |
| Testability | Excellent | Good | Poor |
| Supports immutability? | ✔ Yes | ❌ No | ❌ No |
| Flexibility | Medium | High | Low |
| Code readability | Clear | Moderate | Short but hidden |

### 🏆 Best Exam Answer (3–5 Marks)

> Constructor Injection provides dependencies through the class constructor and is recommended for mandatory dependencies because it supports immutability and better testability. Setter Injection uses a public setter method with `@Autowired`, mainly used for optional dependencies or when the dependency needs to be changed later. Field Injection applies `@Autowired` directly on the variable, making the code short but less testable and not recommended for large applications.

---

## ⭐ @SpringBootApplication & Auto-Configuration

### 💡 What is @SpringBootApplication?

`@SpringBootApplication` is a single annotation that tells Spring Boot to:
- ✔ Start the application
- ✔ Create and manage beans
- ✔ Configure everything automatically

📌 It is a **shortcut** for three combined annotations:

```java
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan
```

### 🔍 Breakdown of the 3 Annotations

#### 1️⃣ @SpringBootConfiguration
- Marks this class as a Spring Boot configuration file
- It is like saying: "Here, setup for the app begins."

#### 2️⃣ @EnableAutoConfiguration
- Spring Boot automatically configures libraries you add
- **Example:**
  - If you add `spring-boot-starter-web`, Boot configures Tomcat + REST automatically
  - If you add JPA, Boot configures Hibernate + datasource automatically

👉 You don't need XML or manual configs

#### 3️⃣ @ComponentScan
- Scans your package for:
  - ✔ `@Component`
  - ✔ `@Service`
  - ✔ `@Repository`
  - ✔ `@RestController`

👉 Automatically identifies beans in your project

### 🧪 Simple Example: Main App

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication   // It does all the setup!
public class DemoApplication {
    
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

### 🧠 What is Auto-Configuration?

Spring Boot automatically configures required components based on the libraries in your project.

📌 **Example:**

**If you add Web dependency, Spring Boot gives:**
- Tomcat server
- REST support
- JSON support
- Dispatcher Servlet

**If you add Spring JPA, Boot gives:**
- Hibernate
- Transaction Manager
- Entity Manager

👉 You don't configure anything manually!

### 🎯 Real-life Example: No Configuration Needed

**Without auto-configuration (old way)** ❌
- You needed an XML file to configure server, bean, MVC.

**With Spring Boot (auto config)** ✔
- Just add dependency and run!

👉 Boot configures everything automatically when the server starts.

### 📌 Short Exam Answer (2.5 or 5 Mark)

> `@SpringBootApplication` is a combination of `@SpringBootConfiguration`, `@EnableAutoConfiguration`, and `@ComponentScan`. It enables Spring Boot to start the application, scan components, and automatically configure beans based on added dependencies. Auto-Configuration reduces manual XML/Java configuration, making application development faster and easier.

---

## 🔧 Ways to Create Spring Beans

### 1️⃣ Creating Bean Inside XML Configuration File (beans.xml)

**Traditional approach** - rarely used in modern Spring Boot

```xml
<!-- beans.xml -->
<beans>
    <bean id="employeeService" class="com.example.EmployeeService"/>
</beans>
```

### 2️⃣ Using @Component Annotation

Most common approach for regular classes

```java
import org.springframework.stereotype.Component;

@Component
public class EmployeeService {
    public String getMessage() {
        return "Service Bean Created";
    }
}
```

**Specialized @Component annotations:**
- `@Service` - for service layer
- `@Repository` - for data access layer
- `@Controller` / `@RestController` - for web layer

### 3️⃣ Using @Bean Annotation

Used when you need more control over bean creation or for third-party classes

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {
    
    @Bean
    public EmployeeService employeeService() {
        return new EmployeeService();
    }
}
```

### 📊 Comparison

| Method | Use Case | Common? |
|--------|----------|---------|
| XML Configuration | Legacy projects | ❌ Rarely used |
| @Component | Your own classes | ✔ Most common |
| @Bean | Third-party libraries, custom setup | ✔ When needed |

---

## 🏛️ Layered Architecture in Spring Boot

### 💡 Simple Definition

Layered Architecture means dividing the project into separate layers, where each layer has a specific responsibility.

It makes the application:
- ✔ Organized
- ✔ Easier to debug
- ✔ Easier to test
- ✔ Easy to maintain

### 🧱 Main Layers in Spring Boot

| Layer | Responsibility | Annotation |
|-------|----------------|------------|
| **Controller** (API Layer) | Handles HTTP requests & responses | `@RestController` |
| **Service** (Business Logic Layer) | Performs business logic/calculations | `@Service` |
| **Repository** (Data Access Layer) | Interacts with the database | `@Repository` or `JpaRepository` |
| **Entity** (Data Layer) | Represents database table as a class | `@Entity` |

### 📌 Data Flow

```
Client → Controller → Service → Repository → Database
```

### 🧪 Simple Example (Employee Application)

#### 1️⃣ Entity Layer
Represents a DB table.

```java
import jakarta.persistence.Entity;
import jakarta.persistence.Id;

@Entity
public class Employee {
    @Id
    private int id;
    private String name;
    
    // Getters and Setters
}
```

#### 2️⃣ Repository Layer
Handles DB operations.

```java
import org.springframework.data.jpa.repository.JpaRepository;

public interface EmployeeRepository extends JpaRepository<Employee, Integer> {
}
```

#### 3️⃣ Service Layer
Contains business logic.

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class EmployeeService {
    
    @Autowired
    private EmployeeRepository repo;
    
    public String saveEmployee(Employee employee) {
        repo.save(employee);
        return "Employee Saved Successfully!";
    }
}
```

#### 4️⃣ Controller Layer
Handles REST API requests.

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

@RestController
public class EmployeeController {
    
    @Autowired
    private EmployeeService service;
    
    @PostMapping("/employee")
    public String addEmployee(@RequestBody Employee employee) {
        return service.saveEmployee(employee);
    }
}
```

### 🔁 Architecture Diagram

```
     🧑‍💻 Client (Browser/Postman)
                  │
                  ▼
      🌐 Controller (@RestController)
                  │
                  ▼
      🧠 Service (@Service)  → Business Logic
                  │
                  ▼
      💾 Repository (@Repository/JpaRepository)
                  │
                  ▼
      🗄️ Database (Employee Table)
```

### 🧠 Exam Short Answer

> Spring Boot uses a layered architecture consisting of Controller, Service, Repository, and Entity layers. The Controller handles requests, Service contains business logic, Repository interacts with the database, and Entity represents database tables. This separation improves maintainability, scalability, and testing.

---

## 🛠️ Maven Build Tool

### 💡 What is Maven?

Maven is a build automation tool used in Java projects to manage dependencies and build applications.

🎯 It helps in:
- ✔ Adding external libraries
- ✔ Compiling code
- ✔ Packaging applications (as `.jar` or `.war`)
- ✔ Running tests
- ✔ Deployment

### 📎 Why do we need Maven?

**Without Maven** ❌
- You must manually download `.jar` files, add them to the project, manage versions.

**With Maven** ✔
- Just write dependency in `pom.xml` and Maven downloads everything automatically.

### 📌 Important: pom.xml

The heart of a Maven project is the file:

```
pom.xml  → Project Object Model
```

📌 It contains:
- Project name & version
- Dependencies (libraries)
- Build plugins

### 🧪 Example of a Dependency (Spring Boot Web)

```xml
<dependencies>
   <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-web</artifactId>
   </dependency>
</dependencies>
```

👉 Maven downloads Spring Boot Web libraries automatically.

### 🔧 Maven Key Functions

| Function | Meaning |
|----------|---------|
| **Compilation** | Converts source code into bytecode |
| **Dependency Management** | Downloads required libraries automatically |
| **Packaging** | Creates JAR/WAR file |
| **Deployment** | Deploys to server or cloud |

### 🧨 Maven Commands (Must Memorize)

| Command | Use |
|---------|-----|
| `mvn compile` | Compiles the project |
| `mvn package` | Creates JAR/WAR |
| `mvn clean` | Deletes `target/` build folder |
| `mvn install` | Adds package to local repo |
| `mvn spring-boot:run` | Runs Spring Boot project |

### 📦 How Spring Boot creates JAR?

Run:
```bash
mvn clean package
```

Then a `.jar` is created in:
```
target/yourappname.jar
```

You can run it:
```bash
java -jar target/yourappname.jar
```

### 🧠 Short Exam Answer (2.5 / 5 Marks)

> Maven is a build automation tool used in Java applications for compilation, dependency management, packaging, and deployment. It uses a central configuration file called `pom.xml` to manage project metadata and external libraries. By defining dependencies inside `pom.xml`, Maven automatically downloads required jars, making project development easier and faster.

---

## 🌐 REST Controller & Handler Methods

### 💡 Simple Definition

A REST Controller handles web requests (like GET, POST, PUT, DELETE) and returns data (usually JSON) to the client.

📌 In Spring Boot, we create a REST Controller using:

```java
@RestController
```

### 🏷️ Handler Methods

**What is a handler method?**

A method inside a REST Controller that handles an HTTP request like GET, POST, PUT, DELETE.

👉 Example:

```java
@GetMapping("/hello")
public String sayHello() {
    return "Hello";
}
```

### 🚦 Most Important HTTP Mappings

| Annotation | Purpose | CRUD |
|------------|---------|------|
| `@GetMapping` | Read data | **READ** |
| `@PostMapping` | Add new data | **CREATE** |
| `@PutMapping` | Update existing data | **UPDATE** |
| `@DeleteMapping` | Delete data | **DELETE** |

### 🧪 Simple Example (All Mappings Together)

```java
import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/users")  // Base URL
public class UserController {
    
    @GetMapping
    public String getUsers() {
        return "All Users";
    }
    
    @PostMapping
    public String addUser() {
        return "User Added";
    }
    
    @PutMapping("/{id}")
    public String updateUser(@PathVariable int id) {
        return "Updated User with id: " + id;
    }
    
    @DeleteMapping("/{id}")
    public String deleteUser(@PathVariable int id) {
        return "Deleted User with id: " + id;
    }
}
```

### 🧠 Exam Short Answer

> `@RestController` is used to create RESTful web services in Spring Boot. Handler methods inside a REST Controller manage HTTP requests using annotations such as `@GetMapping`, `@PostMapping`, `@PutMapping`, and `@DeleteMapping`.

---

## 🔐 @PathVariable and @RequestBody

### 📌 1) @PathVariable

**💡 Simple Explanation:**

`@PathVariable` is used to extract values from the URL. It is used when the value is part of the URL path, like `"/users/10"`.

#### 🧪 Example:

```java
@GetMapping("/users/{id}")
public String getUser(@PathVariable int id) {
    return "User ID: " + id;
}
```

📌 If client calls: `GET /users/10`  
**Output** 👉 `User ID: 10`

✔ `id` comes from the URL itself.

#### 🧠 Why is it Important?

- Used daily in REST APIs
- Always asked in short answers
- Works with GET, PUT, DELETE

### 📌 2) @RequestBody

**💡 Simple Explanation:**

`@RequestBody` is used to read JSON data sent from the client and bind it into a Java object. It is used mainly with POST and PUT methods.

#### 🔎 Example:

**Step 1: Create a Class (Model)**

```java
public class User {
    private String name;
    private int age;
    
    // Getters and Setters
}
```

**Step 2: Use @RequestBody in Controller**

```java
@PostMapping("/users")
public String createUser(@RequestBody User user) {
    return "Created User: " + user.getName();
}
```

📌 If client sends:

```json
{ "name": "Rahul", "age": 22 }
```

✔ **Output** 👉 `Created User: Rahul`

#### 🧠 Why is it Important?

- Used in Create / Update operations
- Always included in 5-mark questions
- Works with JSON → Java Object Conversion

### 🆚 Difference Between @PathVariable & @RequestBody

| Feature | `@PathVariable` | `@RequestBody` |
|---------|-----------------|----------------|
| **Source** | URL path | HTTP request body |
| **Used for** | IDs / single values | JSON input (object) |
| **HTTP Methods** | GET, PUT, DELETE | POST, PUT |
| **Example** | `/users/10` | `{ "name":"Raj" }` |

### 📝 Short Exam Answer (2 / 3 Marks)

> `@PathVariable` extracts values from the URL and is commonly used to read IDs. `@RequestBody` reads JSON data from the request body and converts it into a Java object. `@PathVariable` is mainly used with GET/PUT/DELETE methods, whereas `@RequestBody` is used with POST/PUT for sending object data.

---

## 🛡️ Exception Handling in REST

### 🤔 What is Global Exception Handling?

**Simple Explanation:**

Instead of writing try-catch in every controller, we create **one place** to handle all exceptions.

📌 This one place is called **Global Exception Handler**.

### 🏛️ Real-Life Example

Suppose you are in a college:
- 🎓 Many students (like many API controllers)
- 📩 Complaints (like exceptions)
- 📬 All complaints go to the Principal's office (one handling class)

📌 **Principal's office = Global Exception Handler**

We don't solve problems in each class. We send all errors to a single place.

### 🛡️ How to Handle Exceptions Globally?

We do it using:

**✔ @ControllerAdvice**
→ Says: "This class will handle all errors for every controller."

**✔ @ExceptionHandler**
→ Says: "When this specific error happens, run this method."

### 🧪 Complete Example

#### 🧱 Step 1: Create Custom Exception

```java
public class UserNotFoundException extends RuntimeException {
    public UserNotFoundException(String message) {
        super(message);
    }
}
```

#### 🧱 Step 2: Throw Exception in Controller

```java
@GetMapping("/user/{id}")
public String getUser(@PathVariable int id) {
    if(id != 1) {
        throw new UserNotFoundException("User Not Found!");
    }
    return "Welcome User 1";
}
```

💡 If ID is not 1 → Exception thrown

#### 🧱 Step 3: Handle it Globally (Important)

```java
@ControllerAdvice   // Global Error Handler
public class GlobalExceptionHandler {
    
    @ExceptionHandler(UserNotFoundException.class)
    public String handleUserError(UserNotFoundException ex) {
        return ex.getMessage();   // returns clean message
    }
}
```

📌 We did NOT handle the error in controller.  
📌 The error was handled outside, in GlobalExceptionHandler.

### 🎉 Final Understanding

> Global Exception Handling means we centralize error handling in one class using `@ControllerAdvice`, so we don't write error handling code in every controller.

---

## 📌 Error Response Model (JSON Error Structure)

### 💡 Simple Explanation

When an error happens in a REST API, we should not return plain text like:
```
User not found!
```

Instead, we should return a **well-formatted JSON error**, so the client (Mobile App / Frontend) can read it easily.

### 📦 Standard Error JSON Must Contain:

| Field | Meaning |
|-------|---------|
| `timestamp` | When the error happened |
| `status` | HTTP status code (e.g., 404, 400, 500) |
| `message` | Short explanation of error |
| `path` | URL that caused the error |

✔ These fields make debugging easy.

### 🧪 Example: JSON Error Response

```json
{
  "timestamp": "2025-01-15T14:52:17",
  "status": 404,
  "message": "User not found!",
  "path": "/user/10"
}
```

### 🛠️ How do we return this JSON?

#### 📌 Step 1: Create a Model Class

```java
public class ErrorResponse {
    private String timestamp;
    private int status;
    private String message;
    private String path;
    
    // Constructor
    public ErrorResponse(String timestamp, int status, String message, String path) {
        this.timestamp = timestamp;
        this.status = status;
        this.message = message;
        this.path = path;
    }
    
    // Getters and Setters
}
```

#### 📌 Step 2: Modify Global Handler to Return JSON

```java
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.ControllerAdvice;
import org.springframework.web.bind.annotation.ExceptionHandler;
import jakarta.servlet.http.HttpServletRequest;
import java.time.LocalDateTime;

@ControllerAdvice
public class GlobalExceptionHandler {
    
    @ExceptionHandler(UserNotFoundException.class)
    public ResponseEntity<ErrorResponse> handleUserError(
            UserNotFoundException ex, HttpServletRequest request) {
        
        ErrorResponse error = new ErrorResponse(
                LocalDateTime.now().toString(),
                404,
                ex.getMessage(),
                request.getRequestURI());
        
        return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
    }
}
```

👉 This returns a JSON instead of a plain string.

### 🧠 Short Exam Answer

> The Error Response Model is a standardized JSON structure returned when an exception occurs in a REST API. It usually contains fields like `timestamp`, `status`, `message`, and `path`, helping clients understand and debug errors. A global handler using `@ControllerAdvice` and `@ExceptionHandler` can return this structured JSON.

### 📝 Complete Flow Diagram

```
Client Request → Controller → Exception Thrown
                                    ↓
                          @ControllerAdvice catches it
                                    ↓
                          @ExceptionHandler handles it
                                    ↓
                          Returns ErrorResponse JSON
                                    ↓
                          Client receives structured error
```

### 🏆 10-Mark Question Answer Structure

**Question: Implement global exception handling in Spring Boot REST API with custom exception and error response model.**

**Answer:**

Global exception handling in Spring Boot centralizes error management using `@ControllerAdvice` and `@ExceptionHandler` annotations.

**Step 1: Create Custom Exception**
```java
public class UserNotFoundException extends RuntimeException {
    public UserNotFoundException(String message) {
        super(message);
    }
}
```

**Step 2: Create Error Response Model**
```java
public class ErrorResponse {
    private String timestamp;
    private int status;
    private String message;
    private String path;
    // Constructor, Getters, Setters
}
```

**Step 3: Create Global Exception Handler**
```java
@ControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(UserNotFoundException.class)
    public ResponseEntity<ErrorResponse> handleUserError(
            UserNotFoundException ex, HttpServletRequest request) {
        ErrorResponse error = new ErrorResponse(
            LocalDateTime.now().toString(),
            404,
            ex.getMessage(),
            request.getRequestURI());
        return new ResponseEntity<>(error, HttpStatus.NOT_FOUND);
    }
}
```

**Step 4: Throw Exception in Controller**
```java
@GetMapping("/user/{id}")
public User getUser(@PathVariable int id) {
    if(id != 1) {
        throw new UserNotFoundException("User not found with id: " + id);
    }
    return userService.findById(id);
}
```

This approach ensures all exceptions are handled in one place, returning consistent JSON error responses to clients.

---

## 📌 Key Takeaways

- Focus on **JWT implementation steps** for 10-mark questions
- Practice **exception handling** with @ControllerAdvice
- Understand **JPA annotations** and their usage
- Know the difference between **Query Methods** and **@Query**
- Be familiar with **SecurityFilterChain** configuration

---

## 🔥 Next Steps

- Create detailed notes for each unit
- Practice coding examples for each concept
- Review previous year questions (PYQ) and internal papers
- Build sample projects implementing these concepts

---

## 🎓 JPA Entity and Annotations

### 💡 What is a JPA Entity?

An **Entity** is a Java class mapped to a database table using JPA. Spring Boot uses **JPA + Hibernate** to automatically generate tables based on entity classes.

### 🏷 Common JPA Annotations

| Annotation        | Purpose               | Example                      |
| ----------------- | --------------------- | ---------------------------- |
| `@Entity`         | Marks class as table  | `@Entity class Student {}`   |
| `@Id`             | Primary key           | `@Id int id;`                |
| `@GeneratedValue` | Auto-increment values | `@GeneratedValue`            |
| `@Table`          | Custom table name     | `@Table(name="student_tbl")` |
| `@Column`         | Custom column         | `@Column(name="name")`       |

### 💻 Example Code

```java
import jakarta.persistence.*;

@Entity
@Table(name = "student_tbl")
public class Student {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;

    @Column(name="name")
    private String name;
    
    // Getters and Setters
}
```

### 🧠 Conclusion

> The JPA Entity maps Java objects to relational tables using simple annotations, reducing SQL table creation.

---

## 🗄️ CRUD Operations with JpaRepository

### 💡 Simple Explanation

`JpaRepository` is a JPA interface that provides built-in CRUD methods such as:

* `save()` - Create/Update
* `findAll()` - Read all records
* `findById()` - Read single record
* `delete()` - Delete record

No SQL is required. Spring generates everything automatically.

### 💻 Code Example (CRUD)

#### **Entity**

```java
import jakarta.persistence.*;

@Entity
public class Product {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
    private String name;
    private double price;
    
    // Getters and Setters
}
```

#### **Repository**

```java
import org.springframework.data.jpa.repository.JpaRepository;

public interface ProductRepository extends JpaRepository<Product, Integer> {
}
```

#### **Service**

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import java.util.List;

@Service
public class ProductService {
    @Autowired 
    private ProductRepository repo;
    
    public Product save(Product p) { 
        return repo.save(p); 
    }
    
    public List<Product> list() { 
        return repo.findAll(); 
    }
    
    public Product getById(int id) {
        return repo.findById(id).orElse(null);
    }
    
    public void delete(int id) {
        repo.deleteById(id);
    }
}
```

#### **Controller**

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;
import java.util.List;

@RestController
@RequestMapping("/products")
public class ProductController {
    @Autowired 
    private ProductService service;

    @PostMapping 
    public Product add(@RequestBody Product p) { 
        return service.save(p); 
    }
    
    @GetMapping 
    public List<Product> all() { 
        return service.list(); 
    }
    
    @GetMapping("/{id}")
    public Product getOne(@PathVariable int id) {
        return service.getById(id);
    }
    
    @DeleteMapping("/{id}")
    public String delete(@PathVariable int id) {
        service.delete(id);
        return "Product deleted";
    }
}
```

### 🧠 Conclusion

> CRUD in Spring Data JPA is simplified using `JpaRepository`, making database access faster, easier, and SQL-free.

---

## 🔍 Query Methods in JPA

### 💡 Simple Explanation

Query Methods allow searching data **without writing SQL**, using keywords like `findBy`, `countBy`, `deleteBy`. Spring Data JPA automatically generates queries based on method names.

### 🏷 Supported Keywords Example

| Query                                        | Purpose              | Generated SQL |
| -------------------------------------------- | -------------------- | ------------- |
| `findByName(String name)`                    | Search by name       | `WHERE name=?` |
| `findByPriceGreaterThan(double p)`           | Products above price | `WHERE price>?` |
| `findByCategoryAndPrice(String c, double p)` | AND condition        | `WHERE category=? AND price=?` |
| `countByCategory(String category)`           | Count records        | `SELECT COUNT(*)` |
| `deleteByName(String name)`                  | Delete by name       | `DELETE WHERE name=?` |

### 💻 Example

```java
import org.springframework.data.jpa.repository.JpaRepository;
import java.util.List;

public interface ProductRepository extends JpaRepository<Product, Integer> {
    // Find by category
    List<Product> findByCategory(String category);
    
    // Find products with price greater than value
    List<Product> findByPriceGreaterThan(double price);
    
    // Find by category AND price
    List<Product> findByCategoryAndPrice(String category, double price);
    
    // Find by name containing keyword
    List<Product> findByNameContaining(String keyword);
    
    // Count products by category
    long countByCategory(String category);
}
```

### 🧪 Usage Example

```java
@Service
public class ProductService {
    @Autowired
    private ProductRepository repo;
    
    public List<Product> getExpensiveProducts() {
        return repo.findByPriceGreaterThan(1000.0);
    }
    
    public List<Product> searchByCategory(String category) {
        return repo.findByCategory(category);
    }
}
```

### 🧠 Conclusion

> Query Methods reduce code and allow dynamic searching without writing SQL.

---

## 📝 Custom JPQL and Native SQL Queries

### 💡 Simple Explanation

Sometimes complex queries are required. We can write them manually using:

* **JPQL (Java Persistence Query Language)** - Object-oriented query language
* **Native SQL Queries** - Standard SQL queries

Both are written using `@Query` annotation.

### 💻 Example (JPQL Query)

JPQL uses entity class names and properties instead of table/column names.

```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import java.util.List;

public interface ProductRepository extends JpaRepository<Product, Integer> {
    
    // JPQL Query - uses class name and property names
    @Query("SELECT p FROM Product p WHERE p.category=?1 AND p.price>?2")
    List<Product> searchByCategoryAndPrice(String category, double price);
    
    // JPQL with named parameters
    @Query("SELECT p FROM Product p WHERE p.name LIKE %:keyword%")
    List<Product> searchByKeyword(@Param("keyword") String keyword);
    
    // JPQL for update
    @Modifying
    @Query("UPDATE Product p SET p.price = p.price * 1.1 WHERE p.category=?1")
    void increasePriceByCategory(String category);
}
```

### 💻 Example (Native SQL Query)

Native SQL uses actual database table and column names.

```java
public interface ProductRepository extends JpaRepository<Product, Integer> {
    
    // Native SQL Query - uses table name and column names
    @Query(value="SELECT * FROM product WHERE category=?1", nativeQuery=true)
    List<Product> searchNative(String category);
    
    // Complex native query with JOIN
    @Query(value="SELECT p.* FROM product p JOIN orders o ON p.id=o.product_id WHERE o.status=?1", 
           nativeQuery=true)
    List<Product> findProductsByOrderStatus(String status);
}
```

### 🆚 JPQL vs Native SQL

| Feature | JPQL | Native SQL |
|---------|------|------------|
| Syntax | Uses entity class names | Uses table names |
| Database Independent | ✔ Yes | ❌ No |
| Complex Joins | Moderate | ✔ Better |
| Use Case | Most queries | Complex/specific queries |

### 🧠 Conclusion

> `@Query` allows writing complex SQL/JPQL queries when method names are not enough.

---

## 🔗 JPA Relationships

### 💡 One-To-Many and Many-To-One Relationships

A **One-To-Many** relation means one parent contains many children.

📌 Example: One Department ➝ Many Employees

### 💻 Example Code

#### **Department Entity (One side)**

```java
import jakarta.persistence.*;
import java.util.List;

@Entity
public class Department {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
    
    private String name;

    @OneToMany(mappedBy="dept", cascade=CascadeType.ALL)
    private List<Employee> employees;
    
    // Getters and Setters
}
```

#### **Employee Entity (Many side)**

```java
import jakarta.persistence.*;

@Entity
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;
    
    private String name;

    @ManyToOne
    @JoinColumn(name="dept_id")
    private Department dept;
    
    // Getters and Setters
}
```

### 🔍 Important Annotations

| Annotation | Purpose |
|------------|---------|
| `@OneToMany` | Defines one-to-many relationship (parent side) |
| `@ManyToOne` | Defines many-to-one relationship (child side) |
| `@JoinColumn` | Specifies foreign key column name |
| `mappedBy` | Indicates the owning side of relationship |
| `cascade` | Propagates operations to related entities |

### 💻 Repository Example

```java
public interface DepartmentRepository extends JpaRepository<Department, Integer> {
    Department findByName(String name);
}

public interface EmployeeRepository extends JpaRepository<Employee, Integer> {
    List<Employee> findByDept(Department dept);
}
```

### 💻 Service Example

```java
@Service
public class DepartmentService {
    @Autowired
    private DepartmentRepository deptRepo;
    
    public Department saveDepartmentWithEmployees(Department dept) {
        // Saves department and all employees due to cascade
        return deptRepo.save(dept);
    }
    
    public Department getDepartmentWithEmployees(int id) {
        return deptRepo.findById(id).orElse(null);
    }
}
```

### 🧠 Conclusion

> Relationship mappings allow linking multiple tables as objects, removing the need for manual joins.

---

## 📋 Module 3 Summary

### Key Concepts Covered

1. **JPA Entity & Annotations** - Mapping Java classes to database tables
2. **JpaRepository** - Built-in CRUD operations without SQL
3. **Query Methods** - Dynamic query generation from method names
4. **@Query Annotation** - Custom JPQL and Native SQL queries
5. **JPA Relationships** - One-to-Many and Many-to-One mappings

### 🎯 Exam Focus Areas

- Understand the difference between JPQL and Native SQL
- Know common JPA annotations and their usage
- Practice writing Query Methods
- Understand relationship mappings and cascade operations
- Be able to implement complete CRUD operations

### 💡 Tips for Exam

- Always include `@Entity` and `@Id` annotations in entity classes
- Remember `extends JpaRepository<Entity, IDType>` syntax
- Query Methods follow naming conventions strictly
- Use `@Query` for complex queries
- Understand bidirectional relationships and `mappedBy`

---

**Good luck with your exam preparation! 🎓**