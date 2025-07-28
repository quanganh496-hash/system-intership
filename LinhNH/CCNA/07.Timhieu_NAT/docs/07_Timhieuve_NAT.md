# Tìm hiểu về cơ chế NAT

## Mục lục
1. [Khái quát về cơ chế NAT](#1-khái-quát-về-nat)  
2. [Phân loại NAT](#2-phân-loại-nat)  
  2.1 [Static NAT](#21-static-nat)  
  2.2 [Dynamic NAT](#22-dynamic-nat)  
  2.3 [NAT Overload](#23-pat)  
3. [SNAT - DNAT là gì?](#3-snat-dnat)  
  3.1 [SNAT](#31-snat)  
  3.2 [DNAT](#32-dnat)  
4. [Cơ chế hoạt động](#4-cơ-chế-hoạt-động)  
## 1. Khái quát về NAT
![hinhanh1](/LinhNH/07.Timhieu_NAT/images/nat.png)  
- NAT (Network Address Translation) là kỹ thuật dùng để dịch, chuyển đổi một bộ địa chỉ IP  sang một bộ địa chỉ khác.

Lợi ích:

- Để giúp bảo toàn lượng ipv4 public có giới hạn trên toàn thế giới (NAT có thể chia sẻ kết nối internet cho nhiều máy tính, thiết bị di động khác nhau trong mạng LAN chỉ với một địa chỉ IP public duy nhất).
- Giúp che giấu IP bên trong mạng LAN.
- Giúp kết nối mạng trong với mạng internet. 

## 2. Phân loại NAT
![hinhanh2](/LinhNH/07.Timhieu_NAT/images/phanloai.png)  

### 2.1 Static NAT
![hinhanh2.1](/LinhNH/07.Timhieu_NAT/images/static.png)  


Đây là loại NAT cơ bản nhất và thường được sử dụng để chuyển đổi một địa chỉ IP private trong mạng cục bộ sang một địa chỉ IP public. Trong quá trình chuyển đổi, một địa chỉ IP private được ánh xạ với một địa chỉ IP public, giúp thiết lập kết nối đến những thiết bị trong mạng cục bộ từ bên ngoài mạng. (ánh xạ  1:1)

=> one to one

### 2.2 Dynamic NAT
![hinhanh2.2](/LinhNH/07.Timhieu_NAT/images/dynamic.png)  

Đây là loại NAT phổ biến được sử dụng để chuyển đổi một địa chỉ IP private trong mạng cục bộ sang một địa chỉ IP public. Trong quá trình chuyển đổi, NAT sẽ tạo ra một bảng ánh xạ động giữa những địa chỉ IP private và địa chỉ IP public, cho phép những thiết bị trong mạng cục bộ chia sẻ cùng một địa chỉ IP public.

=> one to one 

### 2.3 PAT
Nhiều địa chỉ truy cập cùng 1 địa chỉ từ bên ngoài có sử dụng thêm Port

![hinhanh2.3](/LinhNH/07.Timhieu_NAT/images/overloading.png)  

NAT Overload (Port Address Translation - PAT), là một dạng của Network Address Translation (NAT) mà cho phép nhiều địa chỉ IP private trong mạng nội bộ được ánh xạ tới một địa chỉ IP public duy nhất bằng cách sử dụng các cổng khác nhau.

Khi một thiết bị trong mạng nội bộ yêu cầu truy cập mạng bên ngoài, router NAT sẽ ánh xạ địa chỉ IP và số cổng của thiết bị nội bộ tới một địa chỉ IP và một số cổng khác nhau trên địa chỉ IP public. Các cổng này được sử dụng để phân biệt các kết nối khác nhau của các thiết bị nội bộ trên cùng một địa chỉ IP public.

=> many to one

## 3. SNAT, DNAT

### 3.1 SNAT
![hinhanh3.1](/LinhNH/07.Timhieu_NAT/images/snat.png) 

SNAT (Source Network Address Translation) là một kỹ thuật dịch địa chỉ IP nguồn nói chung khi kết nối từ địa chỉ IP private sang địa chỉ IP public. Nó ánh xạ địa chỉ IP của máy khách nguồn trong yêu cầu tới bản dịch được xác định trên thiết bị BIG-IP. Đây là dạng NAT phổ biến nhất được sử dụng khi máy chủ nội bộ cần bắt đầu phiên tới máy chủ bên ngoài hoặc máy chủ công cộng.
### 3.2 DNAT
![hinhanh3.2](/LinhNH/07.Timhieu_NAT/images/dnat.png) 

DNAT (Destination Network Address Translation) là một kỹ thuật dịch địa chỉ IP đích nói chung khi kết nối từ địa chỉ IP public sang địa chỉ IP private. Nó thường được sử dụng để chuyển hướng các gói đến địa chỉ IP cụ thể hoặc cổng cụ thể trên địa chỉ IP, trên một máy chủ đơn giản đến một địa chỉ khác, chủ yếu trên máy chủ khác.


## 4. Cơ chế hoạt động

Khi một máy con thực hiện kết nối hoặc gửi dữ liệu tới một máy tính nào đó trên internet, các gói tin sẽ được chuyển đến một NAT router. NAT sử dụng một địa chỉ IP công cộng (public IP address) để đại diện cho các thiết bị trong mạng nội bộ (private IP address). Lúc này gói tin sẽ được gửi đi với địa chỉ ip của NAT.

![hinhanh4](/LinhNH/07.Timhieu_NAT/images/coche_hoatdong.png) 

Khi một gói tin được trả về từ internet hoặc mạng bên ngoài, NAT sẽ chuyển đổi địa chỉ đích của gói tin từ địa chỉ ip public về địa chỉ ip private tương ứng của thiết bị trong mạng nội bộ.

