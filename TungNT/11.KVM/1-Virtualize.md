# 1. Giới thiệu về ảo hóa

- Ảo hóa là một quá trình cho phép máy tính chia sẻ tài nguyên phần cứng của nó với nhiều môi trường được phân tách kỹ thuật số. Mỗi môi trường ảo hóa chạy ngay bên trong các tài nguyên được phân bổ của nó, chẳng hạn như bộ nhớ, sức mạnh xử lý và lưu trữ.
- Phần mềm ảo mô phỏng các chức năng của phần cứng vật lý để chạy đồng thời nhiều máy ảo trên một máy vật lý duy nhất.
- Các doanh nghiệp ứng dụng công nghệ ảo hóa để sử dụng hiệu quả tài nguyên phần cứng của họ và thu về lợi nhuận trên vốn đầu tư lớn hơn.

## Tại sao ảo hoá lại quan trọng?

- Ví dụ tình huống: Xét tình huống một công ty cần máy chủ cho ba chức năng:

1. Lưu trữ email của doanh nghiệp một cách bảo mật

2. Chạy ứng dụng tương tác trực tiếp với khách hàng

3. Chạy các ứng dụng nội bộ của doanh nghiệp

- Mỗi chức năng này có những yêu cầu cấu hình khác nhau:
  - Ứng dụng email cần có nhiều dung lượng lưu trữ hơn và hệ điều hành Windows.
  - Ứng dụng tương tác trực tiếp với khách hàng cần có hệ điều hành Linux và năng lực xử lý cao để xử lý lượng lớn lưu lượng
    truy cập trang web.
  - Ứng dụng nội bộ của doanh nghiệp cần có iOS và bộ nhớ trong (RAM) có dung lượng lớn hơn.

==> Để đáp ứng những yêu cầu này, công ty sẽ thiết lập ba máy chủ vật lý chuyên dụng khác nhau cho từng ứng dụng. Công ty phải tốn một khoản đầu tư ban đầu lớn và thực hiện bảo trì cũng như nâng cấp liên tục cho từng máy một. Công ty cũng không thể tối ưu hóa năng lực điện toán. Công ty thanh toán 100% chi phí bảo trì máy chủ nhưng chỉ sử dụng một phần dung lượng lưu trữ và năng lực xử lý.

- Trong ảo hoá có 2 khái niệm quan trọng là Hypervisor (phần mềm giám sát máy ảo) và Virtual Machine (máy ảo).

## Virtual Machine (VM)

- Máy ảo là một môi trường ảo hóa mà phần mềm giả lập phần cứng máy tính. Máy ảo chạy trên máy chủ vật lý và chia sẻ tài nguyên phần cứng với các máy ảo khác. Mỗi máy ảo có hệ điều hành và ứng dụng riêng biệt. Máy ảo có thể chạy trên máy chủ vật lý hoặc trên máy tính cá nhân.

## Hypervisor

- Hypervisor là một thành phần phần mềm có chức năng quản lý nhiều máy ảo trong một máy tính. Phần mềm này đảm bảo rằng mỗi máy ảo đều nhận được phần tài nguyên theo phân bổ và không can thiệp vào hoạt động của các máy ảo khác. Có hai loại phần mềm giám sát máy ảo. Đó là hypervisor loại 1 và hypervisor loại 2.

![Hypervisor](./images/image.png)

- Hypervisor loại 1 (bare-metal hypervisor): Hypervisor loại 1 chạy trực tiếp trên phần cứng máy tính. Nó không cần hệ điều hành chủ để hoạt động. Hypervisor loại 1 cung cấp hiệu suất tốt hơn và bảo mật cao hơn so với hypervisor loại 2. Ví dụ của hypervisor loại 1 là VMware ESXi, Microsoft Hyper-V, XenServer.
- Hypervisor loại 2 (hosted hypervisor): Hypervisor loại 2 chạy trên hệ điều hành chủ. Nó cần hệ điều hành chủ để hoạt động. Hypervisor loại 2 không cung cấp hiệu suất tốt như hypervisor loại 1. Ví dụ của hypervisor loại 2 là VMware Workstation, Oracle VirtualBox.

# 2. Các loại ảo hóa

## 1. Protection ring

![Protection ring](./images/image6.png)

- Protection ring là một cơ chế bảo vệ được sử dụng trong hệ điều hành để xác định quyền truy cập vào tài nguyên phần cứng của máy tính. Có 4 cấp độ bảo vệ trong protection ring, được đánh số từ 0 đến 3. Mỗi cấp độ có số lượng quyền truy cập giảm dần từ 0 đến 3, nhưng tất cả đều có quyền truy cập vào CPU, RAM, và các tài nguyên khác với mức độ hạn chế khác nhau. Cụ thể:
  - Cấp độ 0: Kernel mode, cấp độ cao nhất, có quyền truy cập vào tất cả tài nguyên phần cứng của máy tính.
  - Cấp độ 1: Device driver mode, có quyền truy cập vào nhiều tài nguyên phần cứng nhưng không thể truy cập vào tài nguyên của kernel mode.
  - Cấp độ 2: Operating system mode, có quyền truy cập vào tài nguyên phần cứng nhưng ít hơn so với cấp độ 1 và không thể truy cập vào tài nguyên của kernel mode và device driver mode.
  - Cấp độ 3: User mode, cấp độ thấp nhất, có quyền truy cập hạn chế vào tài nguyên phần cứng của máy tính, chủ yếu thông qua các dịch vụ hệ điều hành để đảm bảo an toàn và bảo mật.

==> Các loại ảo hoá dựa trên protection ring.

## 2. Full virtualization

![Full virtualization](./images/image7.png)

- Guest OS nằm ở Ring 1 chạy trên máy ảo mà không cần sửa đổi hệ điều hành. Hypervisor chịu trách nhiệm giám sát và quản lý các máy ảo. Guest OS sẽ dịch nhị phân các yêu cầu rồi đưa cho Hypervisor xử lý. Hypervisor sẽ chuyển các yêu cầu này sang các yêu cầu tương ứng với hệ điều hành vật lý.

## 3. Paravirtualization

![Paravirtualization](./images/image8.png)

- Guest OS nằm ở Ring 0, đây là một phương pháp mà phải thay đổi OS ở máy vật lý. Do kernel code ở OS phải chỉnh sửa nên giải pháp này không thể sử dụng ở một số OS mã nguồn đóng như Windows.
- Giải pháp này sẽ tạp thêm 1 lớp Hypervisor nữa để Guest OS giao tiếp bằng hypercall để giao tiếp với hypervisor rồi hypervisor sẽ chuyển yêu cầu này sang phần cứng vật lý.

## 4. Hardware-assisted virtualization

- Hiểu đơn giản là sự kết hợp giữa Full virtualization và Paravirtualization. Các CPU hiện đại hỗ trợ ảo hóa phần cứng, giúp giảm thiểu sự can thiệp của Hypervisor vào quá trình xử lý của CPU.

# 3. Tài liệu tham khảo

- https://mikotech.vn/ao-hoa-la-gi/
- https://aws.amazon.com/vi/what-is/virtualization/
- https://news.cloud365.vn/kvm-tong-quan-ve-virtualization-va-hypervisor/
