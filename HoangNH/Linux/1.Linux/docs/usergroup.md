# Tìm hiểu về user, group trong Linux

## 1.Các quyền của user và group trong Linux

- read: Đối với file, cho phép mở file và đọc. Đối với thư mục, cho phép liệt kê danh sách các file, thư mục trong thư mục đó.
- write: Đối với file, cho phép sửa đổi nội dung file. Đối với thư mục, cho phép thêm,xóa, đổi tên các file trong thư mục đó.
- execute: Đối với file, cho phép thực thi chương trình, tập lệnh. 

![image1](/HoangNH/Linux/1.Linux/image/ls.png)

| |  user | group | other |name|
|:------|:----|:------|:-----|:---|
|d|rwx|---|---|snap|

## 2.user

- Linux OS lưu trữ thông tin người dùng trên file /etc/passwd, với các trường được phân tách nhau bởi dấu ":", theo định dạng

```
username:password:UID:GID:comment:home:shell
```

![image2](/HoangNH/Linux/1.Linux/image/user1.png)

- File /etc/shadow chứa thông tin về mật khẩu của các tài khoản user trên máy, chỉ root user mới có quyền truy cập file này.

- Thêm user:

```
sudo useradd [options] <username>
```
Các options: 

- -m: chỉ định home directory, mặc định là /home/<username>
- -s: chỉ định shell, mặc định là /bin/bash , ví dụ /bin/sh, hoặc nếu không cho user quyền sử dụng shell thì để giá trị /sbin/nologin
- -u: chỉ định user id
- -c: phần này là ghi chú để gợi nhớ user, thường người ta hay để họ tên đầy đủ

- Cập nhật user:

```
sudo usermod [options] <username>
```
Các options:

- -c: chỉnh sửa trường comment
- -d: chỉnh sửa home directory
- -d: thay đổi thời gian hết hạn
- -l: chỉnh sửa tên đăng nhập
- -L: khóa user
- -U: bỏ khóa

- Xóa user:

```
sudo userdel [options] <username>
```

Các options:

- -f: xóa user kể cả có người đang đăng nhập
- -r: xóa user nhưng user phải log out ra từ trước

## 3.group

- File /etc/group lưu trữ thông tin group với định dạng:

```
groupname:password:GID:group members
```

- Thêm group:

```
sudo groupadd [options] <group-name>
```

Options phổ biến nhất là --gid: group id

- Cập nhật group:

```
sudo groupmod [options] <group-name>
```
Các options:

- --gid (-g): cập nhật group id
- --new-name (-n): cập nhật group name

- Xóa group:

```
sudo groupdel <group-name>
```