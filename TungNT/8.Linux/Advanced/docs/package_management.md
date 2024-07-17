# Tổng quan về Package Management

- Các phần cốt lõi của một bản phân phối Linux và hầu hết phần mềm bổ sung được cài đặt thông qua `Package Management`. Mỗi gói chứa các tệp và hướng dẫn cần thiết để làm cho một thành phần phần mềm hoạt động trên hệ thống. Các gói này có thể phụ thuộc lẫn nhau.
- Có 2 loại package management phổ biến:
  - `RPM` (Red Hat Package Manager): Dùng cho các bản phân phối dựa trên Red Hat như Fedora, CentOS, RHEL.
  - `DPKG` (Debian Package): Dùng cho các bản phân phối dựa trên Debian như Ubuntu, Debian.

## Công cụ quản lý gói

| Công cụ cấp cao  | Công cụ cấp thấp | Họ      |
| ---------------- | ---------------- | ------- |
| `yum` (RPM)      | `rpm`            | Red Hat |
| `dnf` (RPM)      | `rpm`            | Red Hat |
| `apt-get` (DPKG) | `dpkg`           | Debian  |
| `apt` (DPKG)     | `dpkg`           | Debian  |

- **Công cụ cấp cao**: Làm việc với các nhóm gói, tải gói từ nhà cung cấp, và xử lý các phụ thuộc.
- **Công cụ cấp thấp**: Xử lý các chi tiết của việc giải nén các gói riêng lẻ, chạy các script, và cài đặt phần mềm chính xác.

## Các lệnh cơ bản

### RPM

- Cài đặt gói: `rpm -ivh package.rpm`
- Xóa gói: `rpm -e package`
- Kiểm tra gói đã cài đặt: `rpm -q package`
- Kiểm tra tất cả gói đã cài đặt: `rpm -qa`
- Kiểm tra thông tin gói: `rpm -qi package`
- Kiểm tra tệp trong gói: `rpm -ql package`
- Kiểm tra gói cài đặt bởi tệp: `rpm -qf file`

### DPKG

- Cài đặt gói: `dpkg -i package.deb`
- Xóa gói: `dpkg -r package`
- Kiểm tra gói đã cài đặt: `dpkg -l package`
- Kiểm tra tất cả gói đã cài đặt: `dpkg -l`
- Kiểm tra thông tin gói: `dpkg -s package`
- Kiểm tra tệp trong gói: `dpkg -L package`
- Kiểm tra gói cài đặt bởi tệp: `dpkg -S file`

## Tổng kết

- Công cụ cấp cao (như apt-get, yum, zypper) quản lý các phụ thuộc và tải xuống các gói, trong khi công cụ cấp thấp (như dpkg, rpm) xử lý các chi tiết kỹ thuật của việc cài đặt và gỡ bỏ các gói.