# SQL Student Database Examples

## Basic Table Structure

CREATE TABLE students (
id INT PRIMARY KEY,
name VARCHAR(100),
score DECIMAL(5, 2)
);

## Sample Data

INSERT INTO students (id, name, score) VALUES
(1, 'majid', 85.5),
(2, 'pankaj', 90.0),
(3, 'taukeer', 78.0),
(4, 'saifuddin', 88.5),
(5, 'raz', 92.0);

## Basic Queries

### Calculate Average Score

SELECT AVG(score) AS average_score
FROM students;

### Count Total Students

SELECT COUNT(id) AS total_students
FROM students;

### Find Highest and Lowest Scores

SELECT MAX(score) AS highest_score, MIN(score) AS lowest_score
FROM students;

## Advanced Queries

### Find Student with Highest Score

SELECT name, score
FROM students
WHERE score = (SELECT MAX(score) FROM students);

### Rank Students by Score

SELECT
id,
name,
score,
RANK() OVER (ORDER BY score DESC) AS rank
FROM students;
