# TaskBridge — ERD Design and PostgreSQL Schema

## 1. Project Overview

This project contains a corrected Entity Relationship Diagram (ERD) and PostgreSQL database schema for TaskBridge.

The database contains three main entities:

- Users
- Projects
- Tasks

The design follows the assignment requirements: users can be assigned multiple tasks, projects can contain multiple tasks, and every task belongs to one user and one project.

## 2. Problems in the Original ERD

The original ER diagram was not available in the assessment material I could access. Therefore, I cannot accurately identify or claim specific mistakes in its attributes or relationships.

The following design checks were considered while preparing the corrected design:

- Each entity should have a primary key.
- Each task should reference an existing user.
- Each task should reference an existing project.
- Required fields should use NOT NULL constraints.
- User email addresses should be unique.
- Relationships should match the assignment requirements.

## 3. Corrected Database Design

### Users

| Column | Data Type | Constraints |
|---|---|---|
| id | SERIAL | PRIMARY KEY |
| name | VARCHAR(100) | NOT NULL |
| email | VARCHAR(255) | UNIQUE, NOT NULL |

### Projects

| Column | Data Type | Constraints |
|---|---|---|
| id | SERIAL | PRIMARY KEY |
| name | VARCHAR(150) | NOT NULL |
| description | TEXT | Optional |

### Tasks

| Column | Data Type | Constraints |
|---|---|---|
| id | SERIAL | PRIMARY KEY |
| title | VARCHAR(200) | NOT NULL |
| user_id | INTEGER | NOT NULL, FOREIGN KEY |
| project_id | INTEGER | NOT NULL, FOREIGN KEY |

## 4. Relationships

- One user can be assigned multiple tasks.
- One project can contain multiple tasks.
- Each task belongs to exactly one user.
- Each task belongs to exactly one project.

## 5. Database Schema Explanation

- **PRIMARY KEY:** Uniquely identifies every record.
- **FOREIGN KEY:** Connects tasks to users and projects.
- **NOT NULL:** Ensures required fields cannot be empty.
- **UNIQUE:** Prevents duplicate user email addresses.

The `tasks` table contains `user_id` and `project_id` as foreign keys to maintain referential integrity.

## 6. Corrected ER Diagram

![Corrected TaskBridge ERD](corrected_erd.png)

## 7. PostgreSQL Setup

Create the database:

```sql
CREATE DATABASE taskbridge;
```

Connect to the database:

```sql
\c taskbridge
```

Execute the schema file:

```sql
\i 'schema.sql'
```

## 8. Verification

The following PostgreSQL commands were used to verify the tables:

```sql
\dt
\d users
\d projects
\d tasks
```

All three tables were successfully created and verified in PostgreSQL.

## 9. Technologies Used

- PostgreSQL
- SQL
- dbdiagram.io
- GitHub