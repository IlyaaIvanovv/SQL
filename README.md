## FamilyMembers

| member_id (key)   | status            | member_name       | birthday
|:------------------|:------------------|:------------------|:------------------
| 1                 | father            | Headley Quincey   | 1960-05-13
| 2                 | mother            | Flavia Quincey    | 1963-02-16
| 3                 | son               | Andie Quincey     | 1983-06-05
| 4                 | daughter          | Lela Quincey      | 1985-06-07
| 5                 | daughter          | Annie Quincey     | 1988-04-10
| 6                 | father            | Ernest Forrest    | 1961-09-11
| 7                 | mother            | Constance Forrest | 1968-09-06
| 8                 | daughter          | Alex Addams       | 2005-01-13

---

### Получить таблицу «FamilyMembers»
```SQL
SELECT * FROM FamilyMembers;
```

### Получить столбец статусов из «FamilyMembers»
```SQL
SELECT status FROM FamilyMembers;
```

### Получить таблицу, где статус `father`
```SQL
SELECT * FROM FamilyMembers
WHERE status = 'father';
```

### Получить таблицу, где статус оканчивается на `er`
```SQL
SELECT * FROM FamilyMembers
WHERE status LIKE '%er';
```

### Получить таблицу, где статус `father` или `mother`
```SQL
SELECT * FROM FamilyMembers
WHERE status = 'father' OR status = 'mother';
```

### Получить таблицу в порядке возрастания по `birthday`, где статус `daughter`
```SQL
SELECT * FROM FamilyMembers
WHERE status = 'daughter'
ORDER BY birthday;
```

### Получить таблицу в порядке убывания по `birthday`, где статус `daughter`
```SQL
SELECT * FROM FamilyMembers
WHERE status = 'daughter'
ORDER BY birthday DESC;
```

### Удалить данные из таблицы «FamilyMembers», где `member_id = 8`
```SQL
DELETE FROM FamilyMembers
WHERE member_id = 8;
```

### Обновить данные в `member_name`, где `member_id = 8`
```SQL
UPDATE FamilyMembers
SET member_name = Alex Forrest
WHERE member_id = 8;
```

### Получить таблицу, где `member_id` в интервале от 5 до 10
```SQL
SELECT * FROM FamilyMembers
WHERE member_id BETWEEN 5 AND 10;
```

---

## Payments

| payment_id (key)  | date              | family_member | good     | amount   | unit_price |
|:------------------|:------------------|:--------------|:---------|:---------|:-----------|
| 1                 | 2005-02-12        | 1             | 1        | 1        | 2000       |
| 2                 | 2005-03-23        | 2             | 1        | 1        | 2100       |
| 3                 | 2005-05-14        | 3             | 4        | 5        | 20         |
| 4                 | 2005-07-22        | 4             | 5        | 1        | 350        |
| 5                 | 2005-07-26        | 4             | 7        | 2        | 150        |
| 6                 | 2005-02-20        | 5             | 6        | 1        | 100        |
| 7                 | 2005-07-30        | 2             | 6        | 1        | 120        |
| 8                 | 2005-09-12        | 2             | 16       | 1        | 5500       |
| 9                 | 2005-09-30        | 5             | 15       | 1        | 230        |
| 10                | 2005-10-27        | 5             | 15       | 1        | 230        |

---

### Получить таблицу с полями `member_name` из таблицы «FamilyMembers» и соответствующие ему поля `unit_price` из таблицы «Payments»
```SQL
SELECT member_name, unit_price FROM FamilyMembers JOIN Payments
ON FamilyMembers.member_id = Payments.payment_id;
```

### Получить сумму столбца `unit_price`
```SQL
SELECT SUM(unit_price) FROM Payments;
```

### Получить среднее арифметическое столбца `unit_price` с названием «Average unit price»
```SQL
SELECT AVG(unit_price) AS "Average unit price" FROM Payments;
```