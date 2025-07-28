# Cài đặt IP tĩnh trên Linux

Để cài đặt IP tĩnh, chúng ta cần chỉnh sửa file 00-installer-config.yaml trong thư mục /etc/netplan

```
sudo nano /etc/netplan/00-installer-config.yaml
```

Sửa lại nội dung file

![image1](/HoangNH/Linux/2.VMWare/image/yaml.png)

Tiếp theo chạy lệnh netplan apply để áp dụng thông số vừa mới thay đổi

```
sudo netplan apply
```

