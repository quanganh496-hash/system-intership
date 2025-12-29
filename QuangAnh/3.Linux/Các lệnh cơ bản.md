# 1.Lệnh thao tác file/thư mục

| **Lệnh** | **Viết đầy đủ (Full form)**    | **Ý nghĩa / Chức năng**                              |
| -------- | ------------------------------ | ---------------------------------------------------- |
| `ls`     | **list**                       | Liệt kê file và thư mục                              |
| `cd`     | **change directory**           | Thay đổi thư mục hiện tại                            |
| `pwd`    | **print working directory**    | Hiển thị đường dẫn thư mục đang đứng                 |
| `mkdir`  | **make directory**             | Tạo mới một thư mục                                  |
| `rmdir`  | **remove directory**           | Xóa thư mục rỗng                                     |
| `rm`     | **remove**                     | Xóa file hoặc thư mục                                |
| `cp`     | **copy**                       | Sao chép file/thư mục                                |
| `mv`     | **move**                       | Di chuyển hoặc đổi tên file/thư mục                  |
| `cat`    | **concatenate**                | Hiển thị nội dung file, nối file                     |
| `touch`  | *(không viết tắt)*             | Tạo file rỗng hoặc cập nhật thời gian chỉnh sửa file |
| `more`   | *(nghĩa: xem nhiều trang)*     | Xem nội dung file theo từng trang                    |
| `less`   | *(nghĩa: xem ít hơn/mượt hơn)* | Xem nội dung file, có thể cuộn lên xuống             |

# 2.Lệnh quản lý user & quyền

| **Lệnh**   | **Viết đầy đủ (Full form)**       | **Ý nghĩa / Chức năng**                                                 |
| ---------- | --------------------------------- | ----------------------------------------------------------------------- |
| `who`      | **who**                           | Hiển thị danh sách user đang đăng nhập                                  |
| `whoami`   | **who am i**                      | In ra tên user hiện tại                                                 |
| `id`       | **identity**                      | Hiển thị UID, GID và group của user                                     |
| `useradd`  | **user add**                      | Tạo mới một tài khoản user                                              |
| `adduser`  | **add user**                      | Tạo user (thường có giao diện tương tác hơn `useradd`)                  |
| `passwd`   | **password**                      | Đặt hoặc đổi mật khẩu cho user                                          |
| `usermod`  | **user modify**                   | Thay đổi thông tin của user (ví dụ đổi shell, group)                    |
| `userdel`  | **user delete**                   | Xóa tài khoản user                                                      |
| `groupadd` | **group add**                     | Tạo mới một group                                                       |
| `groupdel` | **group delete**                  | Xóa group                                                               |
| `groups`   | **groups**                        | Xem user thuộc những group nào                                          |
| `su`       | **substitute user / switch user** | Đổi sang user khác (thường là root)                                     |
| `sudo`     | **superuser do**                  | Thực thi lệnh với quyền quản trị (root)                                 |
| `chmod`    | **change mode**                   | Thay đổi quyền truy cập file/thư mục (r = read, w = write, x = execute) |
| `chown`    | **change owner**                  | Thay đổi chủ sở hữu file/thư mục                                        |
| `chgrp`    | **change group**                  | Thay đổi group sở hữu của file/thư mục                                  |

# 3.Lệnh quản lý hệ thống

| **Lệnh**   | **Viết đầy đủ (Full form)**    | **Ý nghĩa / Chức năng**                                                 |
| ---------- | ------------------------------ | ----------------------------------------------------------------------- |
| `whoami`   | **who am i**                   | Hiển thị user hiện tại đang đăng nhập                                   |
| `uname`    | **unix name**                  | Hiển thị thông tin hệ điều hành (tên kernel, version, kiến trúc…)       |
| `uname -a` | **unix name -all**             | Hiển thị đầy đủ thông tin hệ thống                                      |
| `hostname` | **host name**                  | In ra tên máy (hostname)                                                |
| `top`      | *(không viết tắt)*             | Hiển thị tiến trình đang chạy, mức sử dụng CPU/RAM (giống Task Manager) |
| `htop`     | *(human top)*                  | Phiên bản nâng cao của `top` (màu sắc, dễ đọc hơn)                      |
| `ps`       | **process status**             | Hiển thị danh sách tiến trình đang chạy                                 |
| `kill`     | *(nghĩa: kết thúc)*            | Dừng/kết thúc tiến trình theo PID                                       |
| `df`       | **disk free**                  | Hiển thị dung lượng còn trống của ổ đĩa                                 |
| `du`       | **disk usage**                 | Hiển thị dung lượng file/thư mục đang chiếm                             |
| `free`     | *(nghĩa: bộ nhớ trống)*        | Hiển thị RAM và swap còn trống                                          |
| `uptime`   | *(nghĩa: thời gian hoạt động)* | Hiển thị thời gian máy đã chạy từ lúc khởi động                         |
| `clear`    | *(nghĩa: dọn sạch)*            | Xóa màn hình Terminal, cho gọn gàng                                     |
