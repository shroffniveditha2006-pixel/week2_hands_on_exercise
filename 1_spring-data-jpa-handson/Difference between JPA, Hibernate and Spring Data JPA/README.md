# Hands on 4 - Difference between JPA, Hibernate and Spring Data JPA

## Objective

To understand the differences between Java Persistence API (JPA), Hibernate, and Spring Data JPA, and learn how Spring Data JPA simplifies database operations.

---

## What is JPA?

**Java Persistence API (JPA)** is a Java specification (JSR 338) used for mapping Java objects to relational databases.

### Features
- It is a specification, not an implementation.
- Defines standard APIs for persistence.
- Provides annotations like `@Entity`, `@Table`, `@Id`, and `@Column`.
- Requires an implementation such as Hibernate.

---

## What is Hibernate?

**Hibernate** is an Object Relational Mapping (ORM) framework that implements the JPA specification.

### Features
- Implements JPA.
- Maps Java classes to database tables.
- Handles CRUD operations.
- Requires manual Session and Transaction management.

### Hibernate Example

```java
Session session = factory.openSession();
Transaction tx = session.beginTransaction();

session.save(employee);

tx.commit();
session.close();
```

---

## What is Spring Data JPA?

**Spring Data JPA** is a Spring Framework module built on top of JPA.

It reduces boilerplate code by providing ready-made repository interfaces for performing database operations.

### Features
- Uses JPA implementation internally (usually Hibernate).
- Automatically provides CRUD methods.
- Simplifies transaction management.
- Reduces the amount of code developers write.

### Spring Data JPA Example

```java
public interface EmployeeRepository extends JpaRepository<Employee, Integer> {

}
```

```java
@Autowired
private EmployeeRepository employeeRepository;

@Transactional
public void addEmployee(Employee employee){
    employeeRepository.save(employee);
}
```

---

# Comparison

| Feature | JPA | Hibernate | Spring Data JPA |
|----------|-----|-----------|-----------------|
| Type | Specification | ORM Framework | Spring Module |
| Implementation | No | Yes | Uses Hibernate |
| CRUD Operations | Not directly | Manual | Automatic |
| Boilerplate Code | Medium | High | Very Low |
| Transaction Management | Specification only | Manual | Automatic |
| Repository Support | No | No | Yes |
| Ease of Development | Medium | Good | Excellent |

---

# Relationship

```
Java Application
        │
        ▼
Spring Data JPA
        │
        ▼
JPA Specification
        │
        ▼
Hibernate
        │
        ▼
MySQL Database
```

---

# Advantages

### JPA
- Standard API
- Database independent
- Easy to switch implementations

### Hibernate
- Powerful ORM framework
- Automatic object mapping
- Caching support
- Query Language (HQL)

### Spring Data JPA
- Minimal coding
- Built-in CRUD operations
- Easy pagination and sorting
- Automatic transaction management
- Faster application development

---

# Conclusion

JPA defines the standard for persistence, Hibernate implements that standard, and Spring Data JPA further simplifies database access by providing repository-based programming and reducing boilerplate code.

---

# References

1. https://dzone.com/articles/what-is-the-difference-between-hibernate-and-sprin-1

2. https://www.javaworld.com/article/3379043/what-is-jpa-introduction-to-the-java-persistence-api.html

---

## Author

**Niveditha Shroff**

Cognizant Digital Nurture Program

Hands on 4
