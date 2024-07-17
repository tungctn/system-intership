# Advanced Techniques for MySQL

## Natural Sorting in MySQL

- Mặc định, MySQL sẽ sắp xếp chuỗi theo thứ tự từ điển, không phải theo thứ tự tự nhiên của số. Ví dụ:

  ```sql
  SELECT number
  FROM numbers
  ORDER BY number ASC;
  ```

  - Kết quả trả về sẽ không theo thứ tự tự nhiên của số:

    ```
    1
    10
    100
    2
    20
    200
    ```

- Để sắp xếp theo thứ tự tự nhiên của số, ta có thể sử dụng hàm `CAST` hoặc `CONVERT` để chuyển đổi kiểu dữ liệu của cột sang kiểu số. Ví dụ:

  ```sql
  SELECT number
  FROM numbers
  ORDER BY CAST(number AS UNSIGNED) ASC;
  ```

  - Kết quả trả về sẽ theo thứ tự tự nhiên của số:

    ```
    1
    2
    10
    20
    100
    200
    ```

