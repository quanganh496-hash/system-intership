# Cài đặt VMWare Workstation


## 1.Cài đặt VMWare Workstation

## 2.Cài máy ảo

- Bước 1: Truy cập trang chủ của Ubuntu và tải bộ cài đặt dưới dạng file iso.
- Bước 2: Tại cửa sổ chính của VMware, bạn chọn Create a New Virtual Machine để tiến hành khai báo máy ảo mới.
- Bước 3: Chọn Installer disc image file (iso) và bấm vào Browse để tìm file cài đặt.
- Bước 4: Khai báo ổ cứng ảo.
- Bước 5: Thiết lập dung lượng, cách lưu cho ổ cứng ảo.
- Bước 6: Bấm Finish, VMware sẽ tự động khởi chạy máy ảo cho bạn.
- Bước 7: Thiết lập ngôn ngữ, đặt tên server và password.
- Bước 8: Thiết lập các thông số khác, chờ máy chạy và chọn reboot.

## 3.Các chế độ trong VMWare

Chế độ Bridge: ở chế độ này, card mạng trên máy ảo được gắn vào VMnet0, VMnet0 này liên kết trực tiếp với card mạng vật lý trên máy thật, máy ảo lúc này sẽ kết nối internet thông qua  card mạng vật lý và có chung lớp mạng với card mạng vật lý.

![image1](/HoangNH/Linux/2.VMWare/image/briged.png)

Chế độ NAT: ở chế độ này, card mạng của máy ảo kết nối với VMnet8, VNnet8 cho phép máy ảo đi ra mạng vật lý bên ngoài internet thông qua cơ chế NAT (NAT device). Lúc này lớp mạng bên trong máy ảo khác hoàn toàn với lớp mạng của card vật lý bên ngoài, hai mạng hoàn toàn tách biệt. IP của card mạng máy ảo sẽ được cấp bởi DHCP của VMnet8, trong trường hợp bạn muốn thiết lập IP tĩnh cho card mạng máy ảo bạn phải đảm bảo chung lớp mạng với VNnet8 thì máy ảo mới có thể đi internet.

![image2](/HoangNH/Linux/2.VMWare/image/NAT.png)

Cơ chế Host-only:  máy ảo được kết nối với VMnet có tính năng Host-only, trong trường hợp này là VMnet1 . VMnet Host-only kết nối với  một card mạng ảo tương ứng ngoài máy thật (như đã nói ở phần trên). Ở chế độ này,  các máy ảo không có kết nối vào mạng vật lý bên ngoài hay internet thông qua máy thật , có nghĩa là mạng VMnet Host-only và mạng vật lý hoàn toàn tách biệt. IP của máy ảo được cấp bởi DHCP của VMnet tương ứng. Trong nhiều trường hợp đặc biệt cần cấu hình riêng, ta có thể tắt DHCP trên VMnet và cấu hình IP bằng tay cho máy ảo.

![image3](/HoangNH/Linux/2.VMWare/image/host-only.png)

## 4.Sử dụng chế độ mạng NAT cho các máy ảo để truy cập internet

Bước 1: Để đổi thành IP tĩnh, chúng ta cần chỉnh sửa file 00-installer-config.yaml trong thư mục /etc/netplan

```
sudo nano /etc/netplan/00-installer-config.yaml
```

Bước 2: Sửa lại nội dung file

![image4](/HoangNH/Linux/2.VMWare/image/yaml.png)

Bước 3: Thực hiện ping 

![image5](/HoangNH/Linux/2.VMWare/image/ping.png)

## 5.Sử dụng chế độ card Host-only để 2 máy ảo kết nối với nhau

Bước 1: Cài máy ảo mới và chọn card Host-only
Bước 2: Kiểm tra IP 2 máy ảo 

![image6](/HoangNH/Linux/2.VMWare/image/kt.png)

Máy ảo 1:

![image7](/HoangNH/Linux/2.VMWare/image/ktmay1.png)

Máy ảo 2:

![image8](/HoangNH/Linux/2.VMWare/image/ktmay2.png)

Bước 3: Thực hiện ping

![image9](/HoangNH/Linux/2.VMWare/image/ping2.png)


## 6.Sử dụng 1 card Bridge để từ máy ảo ping ra máy laptop cá nhân

Bước 1: Chọn card Bridge

Bước 2: Kiểm tra IP laptop

![image10](/HoangNH/Linux/2.VMWare/image/lap.png)

Bước 3: Thực hiện ping

![image11](/HoangNH/Linux/2.VMWare/image/ping3.png)
