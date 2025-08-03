Here’s the documentation in a structured format for your **AWS RDS Relational Database Service** project using **MySQL Client (Sqlectron)**:

---

# AWS RDS - Relational Database Service (MySQL)

## 1. **RDS Instance Configuration**

| Setting                 | Value                                                                                                                     |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| **Engine**              | MySQL                                                                                                                     |
| **Public Access**       | Yes (Enable Public Access during RDS creation)                                                                            |
| **Security Group (SG)** | Inbound Rule: TCP 3306 (MySQL/Aurora) from 0.0.0.0/0 *(For testing purpose only. Use CIDR IP restrictions in production)* |
| **Endpoint**            | `database.c3iuq8u6iyy3.us-east-1.rds.amazonaws.com`                                                                       |
| **Port**                | 3306                                                                                                                      |
| **Master Username**     | `admin`                                                                                                                   |
| **Master Password**     | `Admin123`                                                                                                                |

---

## 2. **Database Client Tool**

* **Sqlectron (GUI for MySQL, PostgreSQL, MSSQL)**

  * Download from: [https://sqlectron.github.io/](https://sqlectron.github.io/)

### Sqlectron Connection Configuration:

| Field              | Value                                                             |
| ------------------ | ----------------------------------------------------------------- |
| **Name**           | database                                                          |
| **Server Address** | database.c3iuq8u6iyy3.us-east-1.rds.amazonaws.com                 |
| **Username**       | admin                                                             |
| **Password**       | Admin123                                                          |
| **Port**           | 3306                                                              |
| **Database**       | (Leave blank for initial connection, or enter 'university' later) |

---

## 3. **SQL Queries Execution**

### a. Show existing databases:

```sql
SHOW DATABASES;
```

### b. Create a new database `university`:

```sql
CREATE DATABASE university;
```

### c. Verify the new database is created:

```sql
SHOW DATABASES;
```

### d. Use the `university` database:

```sql
USE university;
```

### e. Create `Course` table:

```sql
CREATE TABLE Course (
    CourseID INT,
    CourseName VARCHAR(1000),
    Rating NUMERIC(2,1)
);
```

### f. Insert course records:

```sql
INSERT INTO Course(CourseID, CourseName, Rating) VALUES
(1, 'AZ-204 Developing Azure solutions', 4.5),
(2, 'AZ-303 Architecting Azure solutions', 4.6),
(3, 'DP-203 Azure Data Engineer', 4.7);
```

### g. View the inserted records:

```sql
SELECT * FROM Course;
```

---

## 4. **Expected Output**

| CourseID | CourseName                          | Rating |
| -------- | ----------------------------------- | ------ |
| 1        | AZ-204 Developing Azure solutions   | 4.5    |
| 2        | AZ-303 Architecting Azure solutions | 4.6    |
| 3        | DP-203 Azure Data Engineer          | 4.7    |

---

## 5. **Important Notes**

* **Public Access** to RDS is for demo/testing; always use **VPC/Subnet restrictions & Bastion Host** for production environments.
* Change default username/password and apply **IAM authentication** for production-grade setups.
* Ensure **security group inbound rules** are restricted to trusted IPs (avoid 0.0.0.0/0 for production).

---

## 6 Delete RDS
- select delete >> untick snapshot, backup
- type delete me 
