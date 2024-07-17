## Bộ nhớ Swap trong Linux

- `Swap` là quá trình trong đó một trang bộ nhớ (page) được sao chép vào một không gian được cấu hình trước trên ổ cứng, gọi là không gian swap, để giải phóng bộ nhớ RAM. Kích thước kết hợp của bộ nhớ vật lý và không gian swap là lượng bộ nhớ ảo khả dụng.

### Lợi ích của Swap

- `Quản lý bộ nhớ khi thiếu RAM`: Khi hệ thống yêu cầu nhiều bộ nhớ hơn số lượng RAM vật lý hiện có, kernel sẽ di chuyển các trang ít sử dụng nhất vào không gian swap và giải phóng RAM cho ứng dụng hiện tại yêu cầu bộ nhớ.
- `Tối ưu hóa sử dụng bộ nhớ`: Các trang bộ nhớ được sử dụng trong quá trình khởi động hệ thống có thể không được sử dụng nữa. Kernel có thể chuyển các trang này vào không gian swap để giải phóng RAM cho các ứng dụng khác hoặc cho cache đĩa.

### Hạn chế của Swap

- `Tốc độ chậm hơn RAM`: Ổ đĩa cứng chậm hơn RAM rất nhiều. Tốc độ truy cập bộ nhớ RAM được đo bằng nanosecond, trong khi tốc độ truy cập đĩa được đo bằng millisecond. Do đó, việc truy cập dữ liệu trên swap chậm hơn rất nhiều so với RAM.
- `Hiệu suất hệ thống giảm`: Nhiều hoạt động swap có thể làm chậm hệ thống đáng kể, tạo ra "cổ chai" khi hệ thống phải liên tục chuyển đổi các trang giữa RAM và swap.

## Các loại không gian swap trong Linux

- Linux hỗ trợ nhiều loại không gian swap khác nhau, bao gồm:
  - `Swap phân vùng`: Swap phân vùng là phân vùng trên ổ cứng được sử dụng làm không gian swap.
  - `Swap file`: Swap file là một tệp trên hệ thống tệp được sử dụng làm không gian swap.

## Kiểm tra không gian swap

- Sử dụng lệnh `swapon -s` để kiểm tra các phân vùng swap và tệp swap đang hoạt động trên hệ thống.

```bash
swapon -s
```


