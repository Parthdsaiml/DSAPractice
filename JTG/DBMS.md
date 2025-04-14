

### **Core Concepts**  
1. **Database (DB)**  
   Organized collection of structured data.  
   *Example:* A school’s database storing student records, courses, and grades.  

2. **DBMS (Database Management System)**  
   Software to create, manage, and query databases (e.g., MySQL, PostgreSQL).  

3. **SQL (Structured Query Language)**  
   Language for interacting with relational databases.  
   *Example:* `SELECT * FROM Students WHERE age > 18;`  

4. **NoSQL**  
   Non-relational databases (e.g., MongoDB for documents, Redis for key-value).  

5. **Relational Database**  
   Stores data in tables with rows (records) and columns (fields).  
   *Example:* `Students` table with columns `id`, `name`, `age`.  

6. **Schema**  
   Structure of the database (tables, columns, relationships).  

---

### **Keys & Relationships**  
7. **Primary Key**  
   Unique identifier for a table row (e.g., `student_id`).  

8. **Foreign Key**  
   Column linking to another table’s primary key (enforces referential integrity).  
   *Example:* `course_id` in `Enrollments` references `Courses` table.  

9. **Composite Key**  
   A primary key made of multiple columns.  
   *Example:* `(student_id, course_id)` in `Enrollments`.  

10. **One-to-Many Relationship**  
    One record in Table A links to many in Table B (e.g., `Department` → `Employees`).  

11. **Many-to-Many Relationship**  
    Requires a junction table (e.g., `Students` ↔ `Courses` via `Enrollments`).  

---

### **SQL Operations**  
12. **JOIN**  
   Combines rows from two or more tables.  
   - **INNER JOIN:** Rows with matching keys.  
   - **LEFT JOIN:** All rows from left table + matches from right.  
   *Example:*  
   ```sql  
   SELECT Students.name, Courses.title  
   FROM Students  
   INNER JOIN Enrollments ON Students.id = Enrollments.student_id  
   INNER JOIN Courses ON Enrollments.course_id = Courses.id;  
   ```  

13. **Index**  
   Improves query speed (like a book index).  
   *Example:* `CREATE INDEX idx_name ON Students(name);`  

14. **Transaction**  
   A sequence of operations that succeed or fail as a unit.  
   *Example:* Transfer money between bank accounts.  

15. **ACID Properties**  
   - **Atomicity:** All-or-nothing execution.  
   - **Consistency:** Valid data state after transaction.  
   - **Isolation:** Concurrent transactions don’t interfere.  
   - **Durability:** Committed data survives crashes.  

---

### **Normalization**  
16. **1NF (First Normal Form)**  
   Eliminate duplicate columns; each cell has atomic values.  
   *Bad Example:* `Courses: "Math, Physics"` → Split into rows.  

17. **2NF (Second Normal Form)**  
   Remove partial dependencies (all non-key columns depend on the full primary key).  

18. **3NF (Third Normal Form)**  
   Remove transitive dependencies (non-key columns depend only on the primary key).  

19. **BCNF (Boyce-Codd Normal Form)**  
   Stricter 3NF: Every determinant is a candidate key.  

---

### **Advanced Concepts**  
20. **Stored Procedure**  
   Pre-written SQL code stored in the DBMS.  
   *Example:*  
   ```sql  
   CREATE PROCEDURE GetStudents()  
   BEGIN  
      SELECT * FROM Students;  
   END;  
   ```  

21. **Trigger**  
   Automatically executes SQL code on events (e.g., `INSERT`, `UPDATE`).  
   *Example:* Log changes to an `Audit` table when a student’s grade is updated.  

22. **View**  
   Virtual table based on a query.  
   *Example:*  
   ```sql  
   CREATE VIEW TopStudents AS  
   SELECT name, GPA FROM Students WHERE GPA > 3.5;  
   ```  

23. **Clustering**  
   Physically reorders data on disk for faster access (e.g., clustered index).  

24. **Partitioning**  
   Splits large tables into smaller chunks (e.g., by date).  

25. **Replication**  
   Copies data across servers for availability (e.g., master-slave replication).  

---

### **NoSQL Concepts**  
26. **Document Database**  
   Stores data as JSON-like documents (e.g., MongoDB).  
   *Example:*  
   ```json  
   { "id": 1, "name": "Alice", "courses": ["Math", "Physics"] }  
   ```  

27. **Key-Value Store**  
   Data stored as key-value pairs (e.g., Redis).  
   *Example:* `SET user:1 "Alice"` → `GET user:1` returns "Alice".  

28. **CAP Theorem**  
   Distributed databases can’t guarantee all three:  
   - **Consistency:** All nodes see the same data.  
   - **Availability:** Every request gets a response.  
   - **Partition Tolerance:** System works despite network failures.  

---

### **Security & Optimization**  
29. **SQL Injection**  
   Attack where malicious SQL is inserted into queries.  
   *Prevention:* Use parameterized queries.  

30. **Sharding**  
   Splits data across multiple databases (horizontal scaling).  

31. **ORM (Object-Relational Mapping)**  
   Maps database tables to application objects (e.g., Hibernate, Django ORM).  

32. **Deadlock**  
   Two transactions block each other.  
   *Example:* Transaction A locks Table 1, Transaction B locks Table 2; both wait for each other.  

---

### **Example Exam Questions**  
1. **Q:** What’s the difference between `INNER JOIN` and `LEFT JOIN`?  
   **A:** `INNER JOIN` returns only matching rows; `LEFT JOIN` returns all rows from the left table + matches.  

2. **Q:** Normalize a table with repeating groups.  
   **A:** Apply 1NF by splitting into separate rows.  

3. **Q:** How do you prevent SQL injection?  
   **A:** Use prepared statements (parameterized queries).  

---

**Quick Revision Tips:**  
- **Normalization:** 1NF → Atomic values, 2NF → No partial deps, 3NF → No transitive deps.  
- **ACID:** Atomic, Consistent, Isolated, Durable.  
- **JOINs:** INNER (matches), LEFT (all left + matches), RIGHT (all right + matches), FULL (all).  

