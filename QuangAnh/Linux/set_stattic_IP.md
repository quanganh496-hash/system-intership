# Trên Ubuntu 24.04
## Cấu hình IP tĩnh với 1 card mạng

Mở file cấu hình netplan (thường nằm trong /etc/netplan/):

     sudo nano /etc/netplan/50-cloud-init.yaml

![alt text](<Ảnh màn hình 2025-09-24 lúc 16.13.01.png>)

ens160: Tên card mạng.

dhcp4: no: tắt DHCP để dùng IP tĩnh.

addresses: - 192.168.1.100/24 địa chỉ IP và subnet mask.

routes: 192.168.1.1 

Chỉnh sửa xong, ấn Esc để thoát khỏi chế độ Insert. Tiếp đó nhập :wq và Enter để lưu cấu hình.

Sau khi thực hiện thay đổi, cần restart để áp dụng thay đổi:

      sudo netplan apply

## Cấu hình IP tĩnh với 2 card mạng
thêm card enp2s0

![alt text](<Ảnh màn hình 2025-09-24 lúc 16.33.22.png>)

Sau khi thực hiện thay đổi, cần restart để áp dụng thay đổi:

      sudo netplan apply


# Trên CentOS Stream 9
## Dùng nmcli (NetworkManager CLI)
### Cấu hình IP tĩnh với 1 card mạng


     ip a

card mạng : ens160

     nmcli con mod ens160 ipv4.addresses 192.168.1.100/24
     nmcli con mod ens160 ipv4.gateway 192.168.1.1
     nmcli con mod ens160 ipv4.dns "8.8.8.8 8.8.4.4"
     nmcli con mod ens160 ipv4.method manual
     nmcli con up ens160

![alt text](<Ảnh màn hình 2025-09-24 lúc 16.47.54-2.png>)

     sudo nmcli connection modify ens160 ipv4.address 192.168.1.100/24
đặt IP tĩnh.

     sudo nmcli connection modify ens160 ipv4.gateway 192.168.1.1
: Đặt gateway.

     sudo nmcli connection modify ens160 ipv4.method manual
: chuyển sang chế độ IP tĩnh.

     nmcli connection up ens160
: Áp dụng thay đổi.

### Cấu hình IP tĩnh với 2 card mạng

thêm card: ens256

     sudo nmcli connection modify ens256 ipv4.address 192.168.1.100/24
đặt IP tĩnh.

     sudo nmcli connection modify ens256 ipv4.gateway 192.168.1.1
: Đặt gateway.

     sudo nmcli connection modify ens256 ipv4.method manual
: chuyển sang chế độ IP tĩnh.

     nmcli connection up ens256

![alt text](<Ảnh màn hình 2025-09-24 lúc 18.07.20-1.png>)

## Cách truyền thống 

lười
