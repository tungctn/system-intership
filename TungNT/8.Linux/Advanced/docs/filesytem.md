# Filesystem Structure (Cấu trúc hệ thống tệp)

## Root Directory (Thư mục gốc)

- Hệ thống tệp trong Linux được tổ chức như một cây (tree), bắt đầu từ thư mục gốc, được ký hiệu là /.
- Filesystem Hierarchy Standard (FHS): Một tiêu chuẩn cung cấp cấu trúc thư mục nhất quán cho hệ thống tệp, giúp các nhà phát triển và quản trị hệ thống dễ dàng quản lý.

## Filesystem Types (Các loại hệ thống tệp)

- Native Linux filesystems: ext3, ext4, btrfs, xfs.
- Filesystems từ hệ điều hành khác: vfat (Windows FAT), ntfs (Windows NTFS), hfs (MacOS).

## Partitions (Phân vùng)

- Mỗi hệ thống tệp đặt trên một phân vùng ổ cứng. Phân vùng giúp tổ chức dữ liệu theo loại và cách sử dụng.
- Các chương trình quan trọng cần thiết để chạy hệ thống thường được lưu trữ trên một phân vùng riêng biệt so với phân vùng chứa các tệp của người dùng thông thường.

## Mounting (Gắn kết)

- Lệnh `mount` được sử dụng để gắn một hệ thống tệp vào cây thư mục hệ thống. Điều này cho phép truy cập vào hệ thống tệp và thư mục trên phân vùng đó từ thư mục gắn kết.

```bash
$ mount /dev/sda5 /mnt (Gắn phân vùng /dev/sda5 vào thư mục /mnt)
```

- Lệnh `umount` được sử dụng để tách hệ thống tệp khỏi thư mục gắn kết.

```bash
$ umount /mnt (Tách phân vùng khỏi thư mục /mnt)
```

- Lệnh `df -Th` hiển thị thông tin về các hệ thống tệp đã gắn kết, bao gồm loại và thống kê về việc sử dụng không gian.

```bash
$ df -Th
Filesystem                 Type      Size  Used Avail Use% Mounted on
/dev/mapper/os-root        xfs        50G  2.0G   48G   4% /
devtmpfs                   devtmpfs  1.8G     0  1.8G   0% /dev
tmpfs                      tmpfs     1.9G  4.0K  1.9G   1% /dev/shm
tmpfs                      tmpfs     1.9G  8.6M  1.8G   1% /run
tmpfs                      tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/mapper/swift01-zone01 xfs        49G   33M   49G   1% /srv/node/z1d1
/dev/mapper/swift02-zone02 xfs        49G   33M   49G   1% /srv/node/z2d1
/dev/sda1                  xfs       497M  167M  331M  34% /boot
/dev/mapper/os-data        xfs        20G  261M   20G   2% /data
```

- /dev/mapper/os-root: Phân vùng chứa hệ thống tệp gốc (/).
- /dev/mapper/os-data: Phân vùng chứa dữ liệu (/data).
- devtmpfs, tmpfs: Hệ thống tệp ảo được sử dụng bởi hệ thống.
- /dev/sda1: Phân vùng chứa dữ liệu khởi động (/boot).
- /dev/mapper/swift01-zone01, /dev/mapper/swift02-zone02: Phân vùng chứa dữ liệu cho dịch vụ OpenStack Swift.

## Home Directories (Thư mục home)

- Mỗi người dùng trên hệ thống Linux có một thư mục home riêng, thường được đặt trong /home.
- Thư mục home chứa các tệp và thư mục cá nhân của người dùng, bao gồm cả cài đặt và cấu hình của các ứng dụng.
- Thư mục root (/) là thư mục home của người dùng root.

## Binary Directories (Thư mục nhị phân)

- /bin: Chứa các lệnh thiết yếu dùng trong chế độ single-user và cần thiết cho tất cả người dùng hệ thống.
- /usr/bin: Chứa các lệnh không cần thiết trong chế độ single-user.
- /sbin: Chứa các lệnh quản trị hệ thống thiết yếu.
- /usr/sbin: Chứa các chương trình quản trị hệ thống ít quan trọng hơn.

## Device Directory (Thư mục thiết bị)

- /dev: Chứa các file thiết bị, mỗi file đại diện cho một thiết bị vật lý hoặc ảo trên hệ thống.
- Các ví dụ về file thiết bị: /dev/sda (ổ cứng), /dev/sr0 (ổ đĩa quang), /dev/null (file null), /dev/zero (file zero).

## Variable Directory (Thư mục biến đổi)

- /var: Chứa các file biến đổi, bao gồm các file log, file tạm, file mail, và các file khác thay đổi thường xuyên khi hệ thống hoạt động.
  - /var/log: Chứa các file log của hệ thống.
  - /var/tmp: Chứa các file tạm thời.
  - /var/mail: Chứa các file mail của người dùng. Nghĩa là nếu bạn nhận mail, nó sẽ được lưu ở đây.
  - /var/ftp: Chứa các file của FTP server.

## System Configuration Directory (Thư mục cấu hình hệ thống)

- /etc: Chứa các file cấu hình hệ thống, bao gồm cả cấu hình của hệ thống và ứng dụng.
- Ví dụ: /etc/passwd (danh sách người dùng), /etc/fstab (danh sách các phân vùng được gắn kết), /etc/hosts (danh sách các máy chủ), /etc/resolv.conf (cấu hình DNS).

## Boot Directory (Thư mục khởi động)

- /boot: Chứa các file cần thiết cho quá trình khởi động hệ thống, bao gồm cả kernel và các file cấu hình khác.
- Các tệp quan trọng: vmlinuz (kernel), initrd.img (initrd), grub (boot loader).
  - /boot/grub: Chứa các file cấu hình của boot loader GRUB.
  - /boot/vmlinuz: Kernel của hệ thống.
  - /boot/initrd.img: Initial RAM disk.
  - /boot/System.map: Bản đồ ký tự của kernel.

## Libraries Directory (Thư mục thư viện)

- /lib: Chứa các thư viện 32-bit cần thiết cho các chương trình trong /bin và /sbin.
- /lib64: Chứa các thư viện 64-bit cần thiết cho các chương trình trong /bin và /sbin.
- lib/modules: Chứa các modules của kernel.

## Additional Directories (Các thư mục bổ sung)

- /opt: Chứa các ứng dụng phần mềm tùy chọn.
- /sys: Hệ thống tệp giả ảo cung cấp thông tin về hệ thống và phần cứng.
- /srv: Dữ liệu cụ thể của trang web được phục vụ bởi hệ thống.
- /tmp: Tệp tạm thời, có thể bị xóa khi khởi động lại.
- /media: Điểm gắn kết cho phương tiện di động như CD, DVD, USB.
- /usr: Ứng dụng, tiện ích và dữ liệu cho nhiều người dùng.
- /usr/include: Tệp tiêu đề để biên dịch ứng dụng.
- /usr/lib: Thư viện cho các chương trình nhị phân.
- /usr/lib64: Thư viện 64-bit cho các chương trình nhị phân.
- /usr/share: Dữ liệu dùng chung cho các ứng dụng, thường không phụ thuộc kiến trúc.
- /usr/src: Mã nguồn, thường là mã nguồn của kernel Linux.
- /usr/local: Dữ liệu và chương trình cụ thể cho máy cục bộ.

## File System Table (Bảng hệ thống tệp)

- Bảng hệ thống tệp (/etc/fstab) chứa thông tin về các phân vùng và cách chúng được gắn kết.
- Ví dụ: [fstab (Italian)](https://wiki.archlinux.org/index.php/Fstab_%28Italiano%29#Dischi_esterni)
