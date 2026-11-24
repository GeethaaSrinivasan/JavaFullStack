# Senior Java Engineer Interview Study Guide
## (Based on 6-7 Years Experience: Java, Spring Boot, Microservices, Cloud, AI Integration)

---

# 1. Core Java

## Q1. Explain the difference between HashMap and ConcurrentHashMap.

### Answer
HashMap is not thread-safe and can cause inconsistent data when multiple threads access it simultaneously. ConcurrentHashMap is designed for concurrent environments and allows multiple threads to read and write safely with minimal locking.

### Example
```java
ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();
map.put("user1", 100);
```

### Key Points
- HashMap → Single-threaded usage
- ConcurrentHashMap → Multi-threaded usage
- Better performance than synchronized collections

---

## Q2. What happens internally when inserting data into HashMap?

### Answer
When a key-value pair is inserted, Java first calculates the hashcode of the key. The hashcode determines the bucket location. If multiple keys map to the same bucket, collision handling occurs using LinkedList or Red-Black Tree (Java 8+).

### Example
```java
Map<Integer, String> map = new HashMap<>();
map.put(101, "John");
```

### Interview Focus
- Hashing
- Buckets
- Load Factor
- Rehashing
- Collision Resolution

---

## Q3. What is the difference between Comparable and Comparator?

### Answer
Comparable is used for natural sorting and requires modifying the class itself. Comparator allows custom sorting logic without modifying the target class.

### Example
```java
Collections.sort(employees,
    Comparator.comparing(Employee::getSalary));
```

### Use Cases
- Sort by Name
- Sort by Salary
- Sort by Joining Date

---

## Q4. Explain Java Stream API.

### Answer
Streams provide a declarative and functional way to process collections. Operations such as filter, map, reduce, and collect make the code concise and easier to maintain.

### Example
```java
List<String> names =
employees.stream()
         .filter(emp -> emp.getSalary() > 100000)
         .map(Employee::getName)
         .toList();
```

### Common Operations
- filter()
- map()
- reduce()
- collect()
- sorted()

---

## Q5. What is CompletableFuture?

### Answer
CompletableFuture is used to perform asynchronous tasks without blocking the main thread. It enables chaining multiple asynchronous operations together.

### Example
```java
CompletableFuture
    .supplyAsync(() -> fetchData())
    .thenApply(data -> process(data));
```

### Benefits
- Non-blocking operations
- Better responsiveness
- Parallel execution

---

# 2. Spring Boot

## Q6. Explain Dependency Injection.

### Answer
Dependency Injection is a design pattern where required dependencies are provided by the Spring Container instead of being created manually. This promotes loose coupling and easier testing.

### Example
```java
@Service
public class UserService {

   private final UserRepository repo;

   public UserService(UserRepository repo) {
      this.repo = repo;
   }
}
```

### Benefits
- Testability
- Maintainability
- Loose Coupling

---

## Q7. What is Spring Boot Auto Configuration?

### Answer
Auto Configuration automatically creates and configures beans based on dependencies found in the classpath. It reduces boilerplate configuration.

### Example
```java
@SpringBootApplication
public class Application {
}
```

### Internally
Contains:
- @Configuration
- @ComponentScan
- @EnableAutoConfiguration

---

## Q8. Explain @Transactional.

### Answer
@Transactional ensures that all database operations within a method succeed together or fail together. If any operation fails, the entire transaction is rolled back.

### Example
```java
@Transactional
public void createOrder() {
   saveOrder();
   updateInventory();
}
```

### Importance
Maintains data consistency.

---

## Q9. Lazy Loading vs Eager Loading.

### Answer
Lazy Loading fetches data only when needed. Eager Loading fetches related data immediately along with the main entity.

### Example
```java
@OneToMany(fetch = FetchType.LAZY)
private List<Order> orders;
```

### Interview Discussion
- N+1 Query Problem
- Performance Implications

---

# 3. Microservices

## Q10. What are Microservices?

### Answer
Microservices divide a large application into smaller independent services. Each service owns its own functionality, deployment lifecycle, and database.

### Benefits
- Independent Deployment
- Scalability
- Fault Isolation

### Example
```text
User Service
Order Service
Payment Service
Notification Service
```

---

## Q11. What is API Gateway?

### Answer
An API Gateway acts as a single entry point for multiple microservices. It handles routing, authentication, rate limiting, and request filtering.

### Flow
```text
Client
   ↓
API Gateway
   ↓
Microservices
```

---

## Q12. Explain Circuit Breaker Pattern.

### Answer
Circuit Breaker prevents repeated requests to failing services. Instead of waiting for timeouts, it returns fallback responses and protects the entire system.

### Example
```text
Order Service
        ↓
Payment Service Down
        ↓
Fallback Response
```

---

## Q13. What is Idempotency?

### Answer
Idempotency ensures that repeated requests produce the same outcome. It prevents duplicate operations during retries.

### Example
```text
Payment Request
Idempotency-Key: 12345
```

Submitting the same request multiple times creates only one payment.

---

# 4. Database & JPA

## Q14. What is the N+1 Query Problem?

### Answer
N+1 occurs when one query fetches parent records and additional queries are executed for each child record, causing performance issues.

### Example
```java
select * from customer;

select * from orders where customer_id=1;
select * from orders where customer_id=2;
```

### Solution
```java
JOIN FETCH
```

---

## Q15. How do you optimize SQL queries?

### Answer
Query optimization involves minimizing scans, reducing unnecessary joins, and creating appropriate indexes. Execution plans help identify bottlenecks.

### Common Techniques
- Add Indexes
- Analyze Explain Plans
- Reduce Full Table Scans
- Cache Frequently Accessed Data

---

## Q16. Explain ACID Properties.

### Answer
ACID ensures reliable database transactions.

### Properties
- Atomicity
- Consistency
- Isolation
- Durability

### Example
Bank Transfer:
```text
Debit Account A
Credit Account B
```

Either both succeed or both fail.

---

# 5. System Design

## Q17. How would you design a URL Shortener?

### Answer
The system generates a unique short URL and stores the mapping. Frequently accessed URLs are cached for faster retrieval.

### Components
```text
Load Balancer
      ↓
Application Servers
      ↓
Database
      ↓
Redis Cache
```

### Considerations
- Scalability
- Caching
- Availability

---

## Q18. Design a Notification Service.

### Answer
Notifications should be processed asynchronously through messaging systems such as Kafka to prevent blocking user requests.

### Flow
```text
User Action
     ↓
Kafka Topic
     ↓
Notification Service
     ↓
Email / SMS / Push
```

### Features
- Retry
- Dead Letter Queue
- Monitoring

---

# 6. Docker & Kubernetes

## Q19. What is Docker?

### Answer
Docker packages applications and dependencies into containers, ensuring consistent execution across environments.

### Example
```dockerfile
FROM openjdk:17
COPY app.jar app.jar
ENTRYPOINT ["java","-jar","app.jar"]
```

### Benefits
- Portability
- Isolation
- Faster Deployment

---

## Q20. Difference Between Docker and Kubernetes.

### Answer

| Docker | Kubernetes |
|----------|-------------|
| Creates Containers | Manages Containers |
| Single Host | Cluster Management |
| Packaging | Orchestration |

### Kubernetes Features
- Auto Scaling
- Self Healing
- Load Balancing

---

# 7. AWS & Cloud

## Q21. Explain AWS Services You Have Used.

### Answer

### EC2
Application Hosting

### S3
Object Storage

### RDS
Managed Databases

### CloudWatch
Monitoring & Alerts

### IAM
Authentication & Authorization

---

## Q22. What is Infrastructure as Code?

### Answer
Infrastructure as Code automates cloud resource creation using configuration files instead of manual setup.

### Example
```text
Terraform
CloudFormation
```

### Benefits
- Repeatability
- Version Control
- Faster Deployment

---

# 8. Production Support & Troubleshooting

## Q23. Describe a Production Issue You Resolved.

### Answer Structure (STAR)

### Situation
API response time increased to 5 seconds.

### Task
Identify root cause.

### Action
Analyzed logs and execution plans.

### Result
Added missing index reducing response time to 300ms.

---

## Q24. How do you diagnose a slow API?

### Answer
Investigate:
1. Application Logs
2. Database Queries
3. External Service Calls
4. JVM Metrics
5. Thread Dumps

### Tools
- Splunk
- ELK
- Prometheus
- Grafana

---

# 9. Behavioral & Leadership

## Q25. How do you conduct code reviews?

### Answer
Code reviews should focus on maintainability, readability, security, performance, and test coverage rather than coding preferences.

### Review Checklist
- Clean Code
- SOLID Principles
- Unit Tests
- Security Vulnerabilities
- Performance Issues

---

## Q26. How do you handle ambiguous requirements?

### Answer
Start by understanding business goals, identifying assumptions, clarifying risks, and documenting decisions before implementation.

### Approach
```text
Requirements
      ↓
Clarifications
      ↓
Design
      ↓
Implementation
      ↓
Feedback
```

---

# Final Revision Checklist

## Core Java
- HashMap Internals
- Streams
- Collections
- CompletableFuture
- Multithreading

## Spring Boot
- Dependency Injection
- Bean Lifecycle
- Transactions
- Spring Security
- JPA/Hibernate

## Microservices
- API Gateway
- Circuit Breaker
- Service Discovery
- Kafka
- Event Driven Architecture

## Database
- ACID
- Indexing
- Query Optimization
- Joins
- N+1 Problem

## Cloud & DevOps
- Docker
- Kubernetes
- AWS
- CI/CD
- Terraform

## System Design
- URL Shortener
- Notification System
- Scalability
- Caching
- Distributed Systems

## Leadership
- Code Reviews
- Technical Decisions
- Production Support
- Mentoring
- Stakeholder Communication