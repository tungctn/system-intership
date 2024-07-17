# Backup data

- Lệnh `rsync` được sử dụng để đồng bộ hóa toàn bộ cây thư mục. Nó sao chép tệp tin giống như lệnh `cp`, nhưng kiểm tra xem tệp tin đã tồn tại hay chưa và chỉ sao chép các tệp tin đã thay đổi, giúp tiết kiệm thời gian.
- `rsync` rất hiệu quả khi sao chép một cây thư mục qua mạng, vì chỉ truyền tải những phần tệp tin đã thay đổi. Thông thường, người ta đồng bộ hóa cây thư mục đích với nguồn, sử dụng tùy chọn `rsync -r` để sao chép tất cả các tệp tin và thư mục dưới cây thư mục được liệt kê là nguồn.

```bash
rsync -ravzh project_ABC /data/backups
```

- Tùy chọn -r để sao chép đệ quy toàn bộ cây thư mục. Nghĩa là sao chép tất cả các tệp tin và thư mục dưới cây thư mục được liệt kê là nguồn.
- Tùy chọn -a để bảo toàn thuộc tính tệp.
- Tùy chọn -v để hiển thị quá trình sao chép.
- Tùy chọn -z để nén dữ liệu trong khi truyền tải.
- Tùy chọn -h để hiển thị thông tin dưới dạng dễ đọc.

## Nén dữ liệu

- Dữ liệu thường được nén để tiết kiệm không gian đĩa và giảm thời gian truyền tải tệp qua mạng. Linux sử dụng nhiều phương pháp nén khác nhau:

| Lệnh  | Sử dụng                                                                                                                                               |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| gzip  | Tiện ích nén Linux được sử dụng nhiều nhất                                                                                                            |
| bzip2 | Tạo ra các tệp tin nhỏ hơn đáng kể so với gzip                                                                                                        |
| xz    | Tiện ích nén hiệu quả không gian nhất được sử dụng trong Linux. Hiện nay, nó được sử dụng bởi kernel.org để lưu trữ các bản lưu trữ của kernel Linux. |
| zip   | Tiện ích nén phổ biến nhất trên Windows, nhưng cũng có thể sử dụng trên Linux.                                                                        |

- Mỗi phương pháp có độ hiệu quả nén khác nhau và thời gian nén khác nhau.

## Tạo tập tin dữ liệu

- Lệnh tar cho phép bạn tạo hoặc giải nén tệp từ một tệp lưu trữ, thường được gọi là tarball. Bạn có thể nén khi tạo tệp lưu trữ và giải nén khi trích xuất nội dung.

```bash
tar -czf project_ABC.tar.gz project_ABC
```

- Tùy chọn -c để tạo một tệp lưu trữ mới.
- Tùy chọn -z để nén tệp lưu trữ với gzip.
- Tùy chọn -f để chỉ định tên tệp lưu trữ.

- Các tuỳ chọn của tar:
  - -c: Tạo một tệp lưu trữ mới.
  - -x: Trích xuất nội dung từ tệp lưu trữ.
  - -t: Hiển thị nội dung của tệp lưu trữ.
  - -z: Nén tệp lưu trữ với gzip.
  - -v: Hiển thị quá trình làm việc.
  - -f: Chỉ định tên tệp lưu trữ.

## Copy disk

- Lệnh `dd` được sử dụng để sao chép toàn bộ ổ đĩa hoặc phân vùng. Lệnh này sao chép từng byte từ nguồn đến đích, không quan tâm đến cấu trúc dữ liệu của ổ đĩa.

```bash
dd if=/dev/sda of=sda.mbr bs=512 count=1
```

- Tùy chọn `if` để chỉ định ổ đĩa nguồn.
- Tùy chọn `of` để chỉ định ổ đĩa đích.
- Tùy chọn `bs` để chỉ định kích thước khối.
- Tùy chọn `count` để chỉ định số lượng khối.

- Để sao chép toàn bộ đĩa:

```bash
dd if=/dev/sda of=/dev/sdb
```

- Để sao chép từ ổ đĩa này sang tệp hình ảnh backup.img rồi sao chép từ tệp hình ảnh này sang ổ đĩa khác:

```bash
dd if=/dev/sda of=backup.img
dd if=backup.img of=/dev/sdb
```
- Cái này sử dụng trong thực tế là xây dựng 1 bản backup để phục hồi dữ liệu khi cần thiết.