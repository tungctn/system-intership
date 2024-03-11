## 1. Giới thiệu về markdown

- Markdown là một ngôn ngữ đánh dấu văn bản thô được tạo ra bởi John Gruber.
- Markdown được thiết kế để dễ viết và dễ đọc dưới dạng văn bản thô và được chuyển thành HTML.
- Markdown thường được sử dụng để tạo tập tin README, viết tin nhắn trong diễn đàn, và tạo văn bản đơn giản để viết blog.

## 2. Cú pháp cơ bản

### 2.1. Tiêu đề

- Để tạo tiêu đề, bạn chỉ cần sử dụng ký tự #. Số lượng ký tự # càng nhiều thì tiêu đề càng nhỏ (1 đến 6 ký tự #).

### 2.2. Highlight chữ

- Dùng 1 kí tự \* để in nghiêng, dùng 2 kí tự ** để in đậm, dùng 3 kí tự \*** để in đậm và in nghiêng.

```
*in nghiêng*
**bôi đậm**
***vừa in nghiêng vừa bôi đậm***
```

Ví dụ: `Markdown` sẽ hiển thị là _Markdown_, `**Markdown**` sẽ hiển thị là **Markdown**, `***Markdown***` sẽ hiển thị là **_Markdown_**.

### 2.3. Link, image

- Để chèn link vào bài viết, ta dùng cú pháp: `[title](đường dẫn)`.

Ví dụ: `[Google](https://www.google.com)` sẽ hiển thị là [Google](https://www.google.com).

- Để chèn ảnh vào bài viết, ta dùng cú pháp: `![alt](đường dẫn)`, trong đó [alt] là alt của ảnh, đường dẫn là đường dẫn của ảnh.

Ví dụ: `![relive](../images/relive.png)` sẽ hiển thị là ảnh dưới đây.

![alt](../images/relive.png)

### 2.4.List, table

- Để tạo danh sách, ta dùng kí tự - hoặc \*.

Ví dụ: Nếu ta viết:

```
- item 1
- item 2
- item 3
```

sẽ hiển thị như sau:

- item 1
- item 2
- item 3

- Để tạo bảng, ta dùng cú pháp:

Kí tự `|` để phân cách giữa các cột, kí tự `-` để phân cách giữa header và body, kí tự `:` để căn lề.

Ví dụ: Nếu ta viết:

```
| Cột 1 | Cột 2 | Cột 3 |
| ----- | ----- | ----- |
| 1     | 2     | 3     |
| 4     | 5     | 6     |
```

sẽ hiển thị như sau:

| Cột 1 | Cột 2 | Cột 3 |
| ----- | ----- | ----- |
| 1     | 2     | 3     |
| 4     | 5     | 6     |

### 2.5. Escape markdown

Thêm kí tự \ trước kí tự markdown muốn escape.

Ví dụ: Nếu ta viết:

```
\*in nghiêng*
```

sẽ hiển thị như sau:

\*in nghiêng\*

