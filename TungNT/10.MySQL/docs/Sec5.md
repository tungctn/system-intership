# Các câu lệnh về Grouping Data

## Câu lệnh `GROUP BY` 

### Mục đích của câu lệnh `GROUP BY`

- Câu lệnh `GROUP BY` được sử dụng để nhóm các dòng dữ liệu dựa trên một hoặc nhiều cột.
- Câu lệnh này thường được sử dụng với các hàm tổng hợp như `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()` để nhóm dữ liệu và thực hiện các phép toán tổng hợp trên các nhóm đó.

### Cú pháp của câu lệnh `GROUP BY`

```sql
SELECT column1, column2, aggregate_function(column3)
FROM table_name
WHERE condition
GROUP BY column1, column2;
```

### Ví dụ về câu lệnh `GROUP BY`

- Ví dụ: Đếm số nhân viên theo từng phòng ban

```sql
SELECT department_id, COUNT(employee_id)
FROM employees
GROUP BY department_id;
```

- Ví dụ: Tính tổng lương của nhân viên theo từng phòng ban

```sql
SELECT department_id, SUM(salary)
FROM employees
GROUP BY department_id;
```

## Câu lệnh HAVING 

### Mục đích của câu lệnh `HAVING`

- Câu lệnh `HAVING` được sử dụng để lọc dữ liệu sau khi đã được nhóm bởi câu lệnh `GROUP BY`. Không giống như câu lệnh `WHERE`, câu lệnh `HAVING` được sử dụng với các hàm tổng hợp như `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`.  

### Cú pháp của câu lệnh `HAVING`

```sql
SELECT column1, column2, aggregate_function(column3)
FROM table_name
WHERE condition
GROUP BY column1, column2
HAVING condition;
```

### Ví dụ về câu lệnh `HAVING`

- Ví dụ: Đếm số nhân viên theo từng phòng ban và chỉ hiển thị các phòng ban có số lượng nhân viên lớn hơn 1

```sql
SELECT department_id, COUNT(employee_id)
FROM employees
GROUP BY department_id
HAVING COUNT(employee_id) > 1;
```

## Câu lệnh ROLLUP

### Mục đích của câu lệnh `ROLLUP`

- Câu lệnh `ROLLUP` được sử dụng để tạo các tổng hợp dữ liệu từ các nhóm dữ liệu. Câu lệnh này tạo ra các tổng hợp từ trên xuống dưới, từ tổng hợp cao nhất đến tổng hợp thấp nhất.

### Cú pháp của câu lệnh `ROLLUP`

```sql
SELECT column1, column2, aggregate_function(column3)
FROM table_name
WHERE condition
GROUP BY ROLLUP(column1, column2);
```

- Câu lệnh trên sẽ tạo ra các tổng hợp dữ liệu từ trên xuống dưới từ cột `column1` đến cột `column2`.


