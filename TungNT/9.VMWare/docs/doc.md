# 1. Cách cài đặt VMWare Workstation Pro 17

- Bước 1: Truy cập vào trang chủ của [VMWare Workstation Pro 17](https://www.vmware.com/products/workstation-pro/workstation-pro-evaluation.html) và tải về bản cài đặt phần mềm (có 2 phiên bản là Windows và Linux).
- Bước 2: Mở file cài đặt vừa tải về và chọn `Next` để tiếp tục.

# 2. Cách tạo máy ảo trên VMWare Workstation Pro 17

- Tải file iso cài đặt hệ điều hành từ trang chủ của hệ điều hành đó. Ví dụ: [Ubuntu](https://ubuntu.com/download/desktop).

![VMWare Workstation Pro 17](../images/create.png)
- Bước 1: Mở VMWare Workstation Pro 17 và chọn `Create a New Virtual Machine`.
- Bước 2: Chọn `Typical` và chọn `Next`.
- Bước 3: Chọn `Installer disc image file (iso)` và chọn `Browse` để chọn file iso cài đặt hệ điều hành.
- Bước 4: Chọn `Next` và nhập thông tin cần thiết cho máy ảo.
- Bước 5: Chọn `Finish` để tạo máy ảo.

# 3. Phân biệt 3 chế độ network trong VMware: NAT, Bridge, Host-only

- **NAT (Network Address Translation)**: Chế độ này cho phép máy ảo kết nối ra ngoài internet thông qua IP của máy chủ. Máy ảo sẽ có IP riêng và không thể truy cập vào máy chủ hoặc các máy ảo khác.
- **Bridge**: Chế độ này cho phép máy ảo kết nối trực tiếp với mạng LAN của máy chủ. Máy ảo sẽ có IP riêng và có thể truy cập vào máy chủ hoặc các máy ảo khác.
- **Host-only**: Chế độ này cho phép máy ảo kết nối với máy chủ và các máy ảo khác thông qua một mạng riêng ảo. Máy ảo sẽ có IP riêng và không thể truy cập ra ngoài internet.


# Tài liệu tham khảo
- https://dummytip.com/giai-ngo-virtualization-phan-5-3-che-do-vmware-network-configuration-ma-ban-nhat-dinh-phai-biet/