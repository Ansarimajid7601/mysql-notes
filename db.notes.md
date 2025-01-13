# SQL Student Database Examples

## Basic Table Structure

```sql
CREATE TABLE students (
id INT PRIMARY KEY,
name VARCHAR(100),
score DECIMAL(5, 2)
);
```

## Sample Data

```sql

INSERT INTO students (id, name, score) VALUES
(1, 'majid', 85.5),
(2, 'pankaj', 90.0),
(3, 'taukeer', 78.0),
(4, 'saifuddin', 88.5),
(5, 'raz', 92.0);
```

## Basic Queries

### Calculate Average Score

```sql

SELECT AVG(score) AS average_score
FROM students;
```

### Count Total Students

```sql

SELECT COUNT(id) AS total_students
FROM students;
```

### Find Highest and Lowest Scores

```sql

SELECT MAX(score) AS highest_score, MIN(score) AS lowest_score
FROM students;
```

## Advanced Queries

### Find Student with Highest Score

```sql

SELECT name, score
FROM students
WHERE score = (SELECT MAX(score) FROM students);
```

### Rank Students by Score

```sql

SELECT
id,
name,
score,
RANK() OVER (ORDER BY score DESC) AS rank
FROM students;
```
