# 📚 Spring Boot Final Exam Study Guide

A comprehensive study plan based on official lecture notes covering Spring Boot fundamentals, REST APIs, JPA, Security, and deployment.

---

## 📖 Table of Contents

- [Unit 1: Spring Boot Core + Beans + Build Tool](#-unit-1-spring-boot-core--beans--build-tool)
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

---

## 📍 Unit 2: REST API + Exception Handling

### 🎯 Must Cover Concepts

- **REST vs SOAP**, URL, Endpoints
- **Handler Methods**: @GetMapping, @PostMapping
- **Input Parameters**: @PathVariable, @RequestBody
- **Global Exception Handling**: @ControllerAdvice + @ExceptionHandler + Custom Model

### 📝 Expected Questions

- What is @RequestBody/@PathVariable?
- Explain Handler Methods with example
- Implement global exception handling (PYQ)

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

**Good luck with your exam preparation! 🎓**