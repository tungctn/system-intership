## File Permissions (Quyền tệp tin)

- Trong Linux, mỗi tệp tin và thư mục đều có một người sở hữu (owner) và một nhóm (group) có liên quan đến tệp tin đó. Các quyền (permissions) được phân thành ba loại: đọc (read), ghi (write), và thực thi (execute). Các quyền này được biểu diễn dưới dạng các chữ cái: r (read), w (write), x (execute).

- Mỗi tệp tin có ba nhóm quyền: người dùng (user), nhóm (group), và người khác (others). Do đó, bạn có ba nhóm quyền với ba quyền trong mỗi nhóm:

  - u (user): Người sở hữu tệp tin.
  - g (group): Nhóm sở hữu tệp tin.
  - o (others): Những người khác.

- Các quyền này được biểu diễn theo ký tự sau: rwxrwxrwx. Trong đó:

  - rwx: Quyền của người dùng (user)
  - rwx: Quyền của nhóm (group)
  - rwx: Quyền của người khác (others)

- Các lệnh liên quan đến quyền tệp tin:

  - `chown`: Dùng để thay đổi người sở hữu của tệp tin hoặc thư mục.
  - `chgrp`: Dùng để thay đổi nhóm sở hữu của tệp tin hoặc thư mục.
  - `chmod`: Dùng để thay đổi quyền truy cập của tệp tin hoặc thư mục.

- Có nhiều cách khác nhau để sử dụng lệnh `chmod`. Ví dụ, để cấp quyền thực thi cho người sở hữu:

  ```
  $ ls -l test1
  -rw-rw-r-- 1 joy caldera 1601 Mar 9 15:04 test1
  ```

  Quyền hiện tại của test1 là `-rw-rw-r--`. Nghĩa là đối với người sở hữu (user) sẽ có quyền đọc và ghi, đối với nhóm (group) cũng có quyền đọc và ghi, và đối với người khác (others) chỉ có quyền đọc.

  ```
    $ chmod u+x test1
    $ ls -l test1
    -rwxrw-r-- 1 joy caldera 1601 Mar 9 15:04 test1
  ```

  Bây giờ test1 có quyền thực thi cho người sở hữu.

## Cách sử dụng shorthand với lệnh `chmod`

- Để đơn giản hóa việc thay đổi quyền truy cập, bạn có thể sử dụng hệ thống số thay cho các ký tự rwx. Hệ thống này dựa trên tổng của các giá trị:

  - 4: Quyền đọc (read)
  - 2: Quyền ghi (write)
  - 1: Quyền thực thi (execute)

- Ví dụ, 7 có nghĩa là quyền đọc + ghi + thực thi, 6 có nghĩa là quyền đọc + ghi, và 5 có nghĩa là quyền đọc + thực thi. Để đặt quyền rwxr-xr-x (người sở hữu: rwx, nhóm: r-x, người khác: r-x):

      ```
      $ chmod 755 test1
      $ ls -l test1
      -rwxr-xr-x 1 joy caldera 1601 Mar 9 15:04 test1
      ```

## Sử dụng `chgrp` để thay đổi nhóm sở hữu

- Bạn có thể thay đổi nhóm sở hữu của một tệp tin bằng cách sử dụng lệnh `chgrp`. Ví dụ:

  ```
  $ ls -l /home/mina/myfile.txt
  -rw-rw-r--. 1 mina caldera 679 Feb 19 16:51 /home/mina/myfile.txt
  $ chgrp root /home/mina/myfile.txt
  $ ls -l /home/mina/myfile.txt
  -rw-rw-r--. 1 mina root 679 Feb 19 16:51 /home/mina/myfile.txt
  ```
