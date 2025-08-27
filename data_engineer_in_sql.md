# 📘 Data Engineering Notes

**Fields:** Data Engineering | Data Architecture | AI & MLOps | DevOps | Financial Engineering | Cloud Computing

---

## 1. Data Engineering with SQL

### 1.1 Views and DISTINCT

Views are virtual tables created to simplify queries and avoid repetition. DISTINCT helps remove duplicate entries.

**Create a view with unique authors:**

```sql
CREATE VIEW library_authors AS
SELECT DISTINCT author AS unique_author
FROM books;
```

**Select from the view:**

```sql
SELECT * FROM library_authors;
```

---

### 1.2 LIMIT

LIMIT is used to restrict the number of rows returned.

**Select first 10 authors:**

```sql
SELECT author AS unique_author
FROM books
LIMIT 10;
```

---

### 1.3 COUNT()

COUNT() is used to count records.

**Count non-null values:**

```sql
SELECT COUNT(birthdate) AS count_birthdates,
       COUNT(name) AS count_names
FROM people;
```

**Count all rows:**

```sql
SELECT COUNT(*)
FROM people;
```

**Count distinct values:**

```sql
SELECT COUNT(DISTINCT birthdate) AS count_distinct_birthdates
FROM people;
```

---

### 1.4 Filtering with WHERE

Filter records using conditions.

**Filter by single condition:**

```sql
SELECT title
FROM films
WHERE release_year > 1960;

SELECT title
FROM films
WHERE release_year <> 1960;
```

**Limit results:**

```sql
SELECT title
FROM films
WHERE release_year > 1960
LIMIT 5;
```

---

### 1.5 Multiple Criteria: OR, AND, BETWEEN

Combine conditions using OR, AND, and BETWEEN.

**Using OR:**

```sql
SELECT *
FROM coats
WHERE color = 'yellow'
   OR length = 'short';
```

**Using AND:**

```sql
SELECT *
FROM coats
WHERE color = 'yellow'
  AND length = 'short';
```

**Using BETWEEN:**

```sql
SELECT *
FROM coats
WHERE buttons BETWEEN 1 AND 5;
```

---

### 1.6 Filtering Text: LIKE, NOT LIKE

Use LIKE to match patterns and NOT LIKE to exclude patterns.

**LIKE for patterns:**

```sql
SELECT name
FROM people
WHERE name LIKE 'Ade%';  -- starts with Ade

SELECT name
FROM people
WHERE name LIKE 'Ev_';   -- starts with Ev followed by any character
```

**NOT LIKE:**

```sql
SELECT name
FROM people
WHERE name NOT LIKE 'A.%';
```

---

### 1.7 Using IN

Check if a value matches a set of values.

**Filter by multiple values:**

```sql
SELECT title
FROM films
WHERE release_year IN (1920, 1930, 1940);
```

---

### 1.8 Handling NULL

Check for missing or non-missing values.

**Check for missing values:**

```sql
SELECT name
FROM people
WHERE birthdate IS NULL;
```

**Check for non-missing values:**

```sql
SELECT COUNT(*) AS no_birthdates
FROM people
WHERE birthdate IS NOT NULL;
```

---

### 1.9 Aggregations: AVG, SUM, MIN, MAX

Aggregate functions help summarize data.

**Average:**

```sql
SELECT AVG(budget) AS avg_budget
FROM films;
```

**Sum:**

```sql
SELECT SUM(budget) AS sum_budget
FROM films;
```

**Minimum:**

```sql
SELECT MIN(budget) AS min_budget
FROM films;
```

**Maximum:**

```sql
SELECT MAX(budget) AS max_budget
FROM films;
```

---

### 1.10 WHERE with Aggregates

Use WHERE to filter before aggregation.

**Filter after aggregation:**

```sql
SELECT MAX(budget) AS max_budget
FROM films
WHERE release_year = 2010;
```

---

### 1.11 Rounding Numbers

Round numbers to control decimal places.

**Round decimals:**

```sql
SELECT ROUND(AVG(budget), 2) AS avg_budget
FROM films
WHERE release_year >= 2010;
```

**Round to whole numbers or multiples of 10/100/1000:**

```sql
SELECT ROUND(AVG(budget), 0) AS avg_budget;    -- whole number
SELECT ROUND(AVG(budget), -5) AS avg_budget;   -- nearest 100,000
```

```
