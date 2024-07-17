# Các câu lệnh Join Tables

## Inner Join

- Câu lệnh `INNER JOIN` được sử dụng để kết hợp các dòng từ hai hoặc nhiều bảng dựa trên một điều kiện so sánh giữa chúng. Ví dụ:

```sql
SELECT employees.first_name, employees.last_name, departments.department_name
FROM employees
INNER JOIN departments
ON employees.department_id = departments.department_id;
```

- Câu lệnh trên sẽ trả về tất cả các dòng và cột từ bảng `employees` và bảng `departments`, trong đó cột `department_id` của bảng `employees` bằng với cột `department_id` của bảng `departments`.

- Câu lệnh `INNER JOIN` cũng có thể kết hợp nhiều bảng. Ví dụ:

```sql
SELECT employees.first_name, employees.last_name, departments.department_name, locations.city
FROM employees
INNER JOIN departments
ON employees.department_id = departments.department_id
INNER JOIN locations
ON departments.location_id = locations.location_id;
```

## Left Join

- Câu lệnh `LEFT JOIN` được sử dụng để kết hợp các dòng từ hai hoặc nhiều bảng dựa trên một điều kiện so sánh giữa chúng. Câu lệnh này trả về tất cả các dòng từ bảng bên trái và các dòng khớp từ bảng bên phải. Ví dụ:

```sql
SELECT employees.first_name, employees.last_name, departments.department_name
FROM employees
LEFT JOIN departments
ON employees.department_id = departments.department_id;
```

- Câu lệnh trên sẽ trả về tất cả các dòng và cột từ bảng `employees`, và các dòng từ bảng `departments` mà cột `department_id` của bảng `employees` bằng với cột `department_id` của bảng `departments`.

## Right Join

- Câu lệnh `RIGHT JOIN` được sử dụng để kết hợp các dòng từ hai hoặc nhiều bảng dựa trên một điều kiện so sánh giữa chúng. Câu lệnh này trả về tất cả các dòng từ bảng bên phải và các dòng khớp từ bảng bên trái. Ví dụ:

```sql
SELECT employees.first_name, employees.last_name, departments.department_name
FROM employees
RIGHT JOIN departments
ON employees.department_id = departments.department_id;
```

- Câu lệnh trên sẽ trả về tất cả các dòng và cột từ bảng `departments`, và các dòng từ bảng `employees` mà cột `department_id` của bảng `employees` bằng với cột `department_id` của bảng `departments`.

## Full Join

- Câu lệnh `FULL JOIN` được sử dụng để kết hợp các dòng từ hai hoặc nhiều bảng dựa trên một điều kiện so sánh giữa chúng. Câu lệnh này trả về tất cả các dòng từ cả hai bảng, dòng khớp từ bảng bên trái và dòng khớp từ bảng bên phải. Ví dụ:

```sql
SELECT employees.first_name, employees.last_name, departments.department_name
FROM employees
FULL JOIN departments
ON employees.department_id = departments.department_id;
```

- Câu lệnh trên sẽ trả về tất cả các dòng và cột từ bảng `employees` và bảng `departments`, trong đó cột `department_id` của bảng `employees` bằng với cột `department_id` của bảng `departments`.

## So sanh giữa các loại Join

- `INNER JOIN`: Trả về các dòng từ cả hai bảng mà có điều kiện so sánh khớp.
- `LEFT JOIN`: Trả về tất cả các dòng từ bảng bên trái và các dòng khớp từ bảng bên phải.
- `RIGHT JOIN`: Trả về tất cả các dòng từ bảng bên phải và các dòng khớp từ bảng bên trái.
- `FULL JOIN`: Trả về tất cả các dòng từ cả hai bảng, dòng khớp từ bảng bên trái và dòng khớp từ bảng bên phải.

## Self Join

- `Self Join` là một trường hợp đặc biệt của `INNER JOIN` hoặc `LEFT JOIN` trong đó một bảng được kết hợp với chính nó. Ví dụ:

```sql
SELECT e1.first_name, e1.last_name, e2.first_name, e2.last_name
FROM employees e1
INNER JOIN employees e2
ON e1.manager_id = e2.employee_id;
```

- Câu lệnh trên sẽ trả về tất cả các dòng và cột từ bảng `employees`, trong đó cột `manager_id` của bảng `employees` bằng với cột `employee_id` của bảng `employees`. Câu lệnh này sẽ trả về tên của nhân viên và tên của người quản lý của họ.

## Cross Join

- `Cross Join` được sử dụng để tạo một kết hợp của mọi dòng từ bảng bên trái với mọi dòng từ bảng bên phải. Ví dụ:

```sql
SELECT employees.first_name, employees.last_name, departments.department_name
FROM employees
CROSS JOIN departments;
```

- Câu lệnh trên sẽ trả về tất cả các dòng và cột từ bảng `employees` và bảng `departments`, trong đó mỗi dòng từ bảng `employees` sẽ được kết hợp với mọi dòng từ bảng `departments`.
