# **Tìm hiểu về IPv4** 
# Mục lục
1. [Khái quát về IPv4](#1-khái-quát-về-ipv4)
2. [Tại sao chỉ có IPv4 mà không có IPv1, v2, v3, v5](#2-tại-sao-chỉ-có-ipv4-mà-không-có-ipv1-v2-v3-v5)
3. [Cấu trúc của IPv4 ](#3-cấu-trúc-của-ipv4)
4. [Các thành phần của IPv4](#4-các-thành-phần-của-ipv4)  
  4.1 [Địa chỉ mạng](#41-địa-chỉ-mạng)  
  4.2 [Địa chỉ máy](#42-địa-chỉ-máy)
5. [Các lớp của IPv4](#5-các-lớp-của-ipv4)  
  5.1 [Lớp A](#51-lớp-a)  
  5.2 [Lớp B](#52-lớp-b)  
  5.3 [Lớp C](#53-lớp-c)  
  5.4 [Lớp D](#54-lớp-d)  
  5.5 [Lớp E](#55-lớp-e)  
6. [Phân biệt IP public và IP private](#6-phân-biệt-ip-public---ip-private)  
7. [Cách chia địa chỉ IPv4](#7-cách-chia-địa-chỉ-ipv4)  
8. [Phân biệt multicast và broadcast](#8-phân-biệt-multicast---broadcast)
9. [Tìm hiểu về subnet, subnet mask, prefix](#9-tìm-hiểu-về-subnet-subnet-mask-prefix)
10. [Thực hành chia mạng](#10-thực-hành-chia-mạng-ip)
## 1. Khái quát về IPv4
![hinh_1](/LinhNH/04.TimhieuIpV4/images/ipv4.png)
- **`Địa chỉ IPv4`** (Internet Protocol version 4) được phát triển vào những năm 1970 và trở thành mạng lưới đầu tiên kết nối tất cả các máy tính trên toàn thế giới. Là một địa chỉ duy nhất được sử dụng để xác định một thiết bị trong mạng Internet.
- **`IPv4`** được ứng dụng trong các hệ thống chuyển mạch gói. Vai trò của nó là định hướng dữ liệu truyền đi. Khi truyền đi các gói tin, giao thức này chỉ đảm bảo phần truyền tải mà không để ý đến thứ tự truyền gói tin hoặc vấn đề gói tin có đến đích hay không, có lặp lại ở máy đích hay không. 
## 2. Tại sao chỉ có IPv4 mà không có IPv1, v2, v3, v5
IPv4 là phiên bản đầu tiên và phổ biến nhất của giao thức Internet Protocol (IP), và không có IPv1, IPv2, IPv3, IPv5 là do:
- IPv1 không được đưa ra công khai:
  - Trong quá trình phát triển ban dầu của IP, nhiều phiên bản thử nghiệm đã được thực hiện, nhưng không có phiên bản cụ thể nào được công nhận là IPv1.
  - IPv4 được phát hiện và công bố trong RFC 791 vào năm 1981, và đó là phiên bản IP đầu tiên được sử dụng rộng rãi trên Internet.
- IPv2, IPv3 không phát triển thành công: 
  - Có một số nỗ lực trong quá khứ để phát triển các phiên bản mới của giao thức IP, nhưng chúng không đạt được sự thành công như IPv4
  - Thay vì tiếp tục phát triển IPv2, IPv3, các nhà nghiên cứu và kỹ sư đã quyết định tiếp tục cải tiến và mở rộng IPb4, đồng thời làm việc trên các phiên bản mới hơn như IPv5 và sau này là IPv6.
- IPv5 đã được sử dụng cho một mục đích khác: 
  - Mặc dù không có một phiên bản chính thức của IPv5, nhưng có một phiên bản gọi là IPv5 đã được phát triển nhưng không bao giờ được triển khai như một giao thức Internet chính thống.
  - Thay vào đó, IPv5 thường được sử dụng để đề cập đến giao thức Internet Stream Protocol (ST), được phát triển cho việc truyền dữ liệu streaming âm thanh và video, và không phải là một phiên bản tiếp theo của IPv4.     

_Tóm lại, việc chỉ có IPv4 như là một phiên bản chính thức đầu tiên của giao thức IP là kết quả của quá trình phát triển và tiến hóa của Internet Protocol trong suốt thời gian._
## 3. Cấu trúc của  IPv4
Về cấu tạo, **địa chỉ IPv4** sẽ có 32 bit và được biểu diễn dưới dạng 4 khối, mỗi khối chứa 8 bit, được ngăn cách bằng dấu (.) và được biểu diễn thành một dãy số nhị phân. Mỗi khối khối như vậy sẽ được gọi là một _octet_.
![hinh_3](/LinhNH/04.TimhieuIpV4/images/cautruc.png)
## 4. Các thành phần của IPv4
### 4.1 Địa chỉ mạng
**Địa chỉ mạng** (Network Address): Phần này đại diện cho mạng mà thiết bị đang kết nối tới. Đây là phần chung cho tất cả các thiết bị trong cùng một mạng. Trong một mạng lớn hơn, các số đầu tiên trong địa chỉ IPv4 sẽ thường được giữ nguyên để đại diện cho mạng đó. Ví dụ: Trong địa chỉ 192.168.1.1, "192.168.1" là địa chỉ mạng.
### 4.2 Địa chỉ máy
**Địa chỉ máy** (Host Address): Phần này đại diện cho thiết bị cụ thể trong mạng. Đây là phần dành riêng cho mỗi thiết bị trong mạng. Trong ví dụ trên, "1" là phần địa chỉ của máy trong mạng.
## 5. Các lớp của IPv4
Trong địa chỉ IPv4, các lớp chính xác phân biệt và định rõ phạm vi và mục đích của mỗi địa chỉ IP. Cụ thể, có ba lớp chính (A, B, C) và 2 lớp phụ (D, E)
### 5.1 Lớp A

![hinh_5.1](/LinhNH/04.TimhieuIpV4/images/lopA.png)

Địa chỉ lớp A có phần mạng là 8 bit đầu và phần host là 24 bit sau. Bit đầu tiên của phần mạng luôn là 0.
Lớp A sẽ có các địa chỉ mạng từ 1.0.0.0 đến 126.0.0.0 và mỗi mạng sẽ có 224 địa chỉ host (loại trừ địa chỉ mạng và địa chỉ broadcast).  
Mạng loopback sẽ là 127.0.0.0.

### 5.2 Lớp B

![hinh_5.2](/LinhNH/04.TimhieuIpV4/images/lopB.png)

Địa chỉ lớp B có phần mạng là 16 bit đầu và phần host là 16 bit sau. 2 bit đầu tiên của phần mạng luôn là 1.0.
Lớp B sẽ có các địa chỉ mạng từ 128.0.0.0 đến 191.255.0.0 và mỗi mạng sẽ có 214 địa chỉ host (loại trừ địa chỉ mạng và địa chỉ broadcast).

### 5.3 Lớp C

![hinh_5.3](/LinhNH/04.TimhieuIpV4/images/lopC.png)

Địa chỉ lớp C có phần mạng là 24 bit đầu và phần host là 8 bit sau. 3 bit đầu tiên của phần mạng luôn là 1.1.0.
Lớp C sẽ có các địa chỉ mạng từ 192.0.0.0 đến 223.255.255.0 và mỗi mạng sẽ có 26 địa chỉ host (loại trừ địa chỉ mạng và địa chỉ broadcast).

### 5.4 Lớp D

Lớp D

Các địa chỉ trong lớp D là những địa chỉ multicast bao gồm 224.0.0.0 đến 239.255.255.255.

### 5.5 Lớp E

Lớp E

Các địa chỉ trong lớp E có vai trò dùng để dự phòng, bao gồm những địa chỉ từ 240.0.0.0 trở đi. 

## 6. Phân biệt ip Public - ip Private
- Địa chỉ IP được phân thành hai loại: private và public.
![hinh_6](/LinhNH/04.TimhieuIpV4/images/ip_public_private.png)

  - Private: chỉ được sử dụng trong mạng nội bộ (mạng LAN), không được định tuyến trên môi trường Internet. Có thể được sử dụng lặp đi lặp lại trong các mạng LAN khác nhau.
  - Public: là địa chỉ IP sử dụng cho các gói tin đi trên môi trường Internet, được định tuyến trên môi trường Internet, không sử dụng trong mạng LAN. Địa chỉ public phải là duy nhất cho mỗi host tham gia vào Internet. 
- Dải địa chỉ private (được quy định trong RFC 1918):  
Lớp A: 10.x.x.x  
Lớp B: 172.16.x.x -> 172.31.x.x  
Lớp C: 192.168.x.x  
- Kỹ thuật NAT (Network Address Translation) được sử dụng để chuyển đổi giữa IP private và IP public.
- Ý nghĩa của địa chỉ private: được sử dụng để bảo tồn địa chỉ IP public đang dần cạn kiệt.
## 7. Cách chia địa chỉ IPv4
## 8. Phân biệt multicast - broadcast
![hinh_8](/LinhNH/04.TimhieuIpV4/images/broadcast-multicast.png)

|Tính năng | Multicast |Broadcast|
|---|----------------|----|
|Cách thức truyền gói tin|Cho phép gửi dữ liệu đến tập hợp thiết bị được xác định trong mạng|Cho phép gửi các gói tin tới tất cả các thiết bị trong một mạng có cùng dải mạng|
|Địa chỉ|Sử dụng một loạt các địa chỉ đặc biệt thuộc vào dải từ 224.0.0.0 đến 239.255.255.255|Thường là địa chỉ mạng với tất cả các bit địa chỉ máy đều là 1. Ví dụ, nếu địa chỉ mạng là 192.168.1.0, thì địa chỉ broadcast sẽ là 192.168.1.255|
|Sử dụng|Các ứng dụng như video streaming, IPTV, giao thức OSPF, IGMP|Sử dụng cho các tin nhắn hoặc yêu cầu mà tất cả các thiết bị trong mạng cần nhân được (DHCP, ARP)
|Bảo mật|Bảo mật trung bình vì dữ liệu được gửi đến một nhóm thiết bị cụ thể trong mạng|Bảo mật trung bình vì dữ liệu được gửi đến tất cả các thiết bị trong mạng|  
## 9. Tìm hiểu về subnet, subnet mask, prefix
_Các khái niệm subnet, subnet mask và prefix đều liên quan đến cách chia mạng để quản lý và tăng hiệu suất mạng. Chúng là các khái niệm cơ bản trong lĩnh vực mạng máy tính và rất quan trọng trong việc cấu hình và quản lý mạng._
### 9.1 Subnet
- Mạng con (Subnet) là một phần của một mạng lớn được chia nhỏ thành các phần nhỏ hơn để quản lý hiệu quả và để tăng cường bảo mật. Khi một mạng lớn được chia thành các mạng con, mỗi mạng con có thể được quản lý một cách độc lập và tối ưu hóa cho mục đích cụ thể của nó.
- Mạng con thường được định nghĩa bằng một phạm vi các địa chỉ IP liên tiếp, cùng với một subnet mask hoặc độ dài tiền tố (prefix length).
### 9.2 Subnet mask
- Subnet mask là một số dãy bit được sử dụng để xác định phần của địa chỉ IP mà là phần mạng và phần nào là phần host. Nó được sử dụng cùng với địa chỉ IP để xác định mạng con mà một thiết bị hoặc máy tính cụ thể nằm trong.
- Subnet mask thường được biểu diễn dưới dạng dãy số thập phân, gồm bốn octet (mỗi octet từ 0 đến 255), trong đó mỗi octet biểu diễn 8 bit. Các bit 1 trong subnet mask đại diện cho phần mạng của địa chỉ IP, trong khi các bit 0 đại diện cho phần host.
### 9.3 Prefix 
- Số prefix, hay độ dài tiền tố (prefix length), là một phần của hệ thống CIDR (Classless Inter-Domain Routing), được sử dụng để xác định mạng con của một địa chỉ IP. Số prefix định nghĩa số lượng bit trong subnet mask mà được sử dụng để xác định mạng con.
- Trong CIDR, địa chỉ IP được biểu diễn bằng cách kết hợp địa chỉ IP cùng với số prefix, thường là dưới dạng "/xx" (ví dụ: /24), trong đó "xx" là số bit trong subnet mask được sử dụng cho mạng con. Ví dụ, nếu bạn thấy một địa chỉ IP được kèm theo "/24", điều này có nghĩa là subnet mask tương ứng là 255.255.255.0 (vì có 24 bit mạng và 8 bit host).
- Số prefix giúp biểu diễn mạng con một cách ngắn gọn và tiện lợi hơn, đồng thời cung cấp thông tin chi tiết về cách mạng con được chia. Nó cũng được sử dụng trong việc quản lý và cấu hình mạng, giúp quản trị viên mạng hiểu được cấu trúc mạng và phân biệt mạng con một cách dễ dàng.  

## 10. Thực hành chia mạng IP
> Bài tập 2.5  

__Địa chỉ có thể dùng cho host:__
- 150.100.255.255  
- 175.100.255.18  
- 195.234.253.0  
- 100.0.0.23

__Địa chỉ không thể dùng cho host:__  
- 188.258.221.176 : vì octet thứ hai là 258 lớn hơn 255  
- 127.34.25.189 : vì đây là địa chỉ loopback  
- 224.156.217.73 : vì đây là địa chỉ lớp D dùng làm địa chỉ   multicast

> Bài tập 4.6.1        

__a/ 192.168.2.0/24 mượn 5 bit__   
- số bit mượn là 5, số bit mạng bây giờ là 24 + 5 = 29 
- số bit host còn lại là 32 - 29 = 3
- số subnet có thể có 2^5 = 32
- số host trên  mỗi subnet 2^3 - 2 = 6
- các địa chỉ mạng sẽ có octet bị chia cắt (octet thứ 4) là bội số của 8
- liệt kê các mạng như sau:
  + 192.168.2.0/29 -> địa chỉ mạng
  + 192.168.2.1/29 -> địa chỉ host đầu  
  .....
  + 192.168.2.6/29 -> địa chỉ host cuối
  + 192.168.2.7/29 -> địa chỉ broadcast  
  -----
  + 192.168.2.8/29 -> địa chỉ mạng
  + 192.168.2.9/29 -> địa chỉ host đầu  
  .....
  + 192.168.2.14/29 -> địa chỉ host cuối
  + 192.168.2.15/29 -> địa chỉ broadcast        
  ----- 
  _....._
  -----
  + 192.168.2.248/29 -> địa chỉ mạng
  + 192.168.2.249/29 -> địa chỉ host đầu  
  .....
  + 192.168.2.254/29 -> địa chỉ host cuối  
  + 192.168.2.255/29 -> địa chỉ broadcast
- subnet mask được sử dụng là 255.255.255.248
- số prefix là 29

__b/ 192.168.12.0/24 mượn 3 bit__   
- số bit mượn là 3, số bit mạng bây giờ là 24 + 3 = 27 
- số bit host còn lại là 32 - 27 = 5
- số subnet có thể có 2^3 = 8
- số host trên  mỗi subnet 2^5 - 2 = 30
- các địa chỉ mạng sẽ có octet bị chia cắt (octet thứ 4) là bội số của 32
- liệt kê các mạng như sau:
  - 192.168.12.0/27 -> địa chỉ mạng  
  - 192.168.12.1/27 -> địa chỉ host đầu  
.....
  - 192.168.12.30/27 -> địa chỉ host cuối  
  - 192.168.12.31/27 -> địa chỉ broadcast  
  -----  
  _....._    
  -----
  - 192.168.12.224/27 -> địa chỉ mạng  
   - 192.168.12.225/27 -> địa chỉ host đầu   
	..... 
  - 192.168.12.254/27 -> địa chỉ host cuối  
  - 192.168.12.255/27 -> địa chỉ broadcast  
- subnet mask được sử dụng là 255.255.255.224  
- số prefix là 27  

__c/ 172.16.2.0/24 mượn 2 bit__  
- số bit mượn là 2, số bit mạng bây giờ là 24 + 2 = 26 
- số bit host còn lại là 32 - 26 = 6
- số subnet có thể có 2^2 = 4
- số host trên  mỗi subnet 2^6 - 2 = 62
- các địa chỉ mạng sẽ có octet bị chia cắt (octet thứ 4) là bội số của 64
- liệt kê các mạng như sau:  
  - 172.16.2.0/26 -> địa chỉ mạng
  - 172.16.2.1/26 -> địa chỉ host đầu  
  .....    
  - 172.16.2.62/26 -> địa chỉ host cuối
  - 172.16.2.63/26 -> địa chỉ broadcast
  -----
  _....._
  ----- 
  - 172.16.2.192/26 -> địa chỉ mạng
  - 172.16.2.193/26 -> địa chỉ host đầu  
  .....  
  - 172.16.2.254/26 -> địa chỉ host cuối
  - 172.16.2.255/26 -> địa chỉ broadcast
- subnet mask được sử dụng là 255.255.255.192
- số prefix là 26    

__d/ 172.16.0.0/16 mượn 3 bit__
- số bit mượn là 3, số bit mạng bây giờ là 16 + 3 = 19 
- số bit host còn lại là 32 - 19 = 13
- số subnet có thể có 2^3 = 8
- số host trên  mỗi subnet 2^13 - 2
- địa chỉ mạng có octet thứ 3 là bội số của 32 (octet này bị mượn 3 bit)
- liệt kê các mạng như sau:
  - 172.16.0.0/19 -> địa chỉ mạng
  - 172.16.0.1/19 -> địa chỉ host đầu  
  .....  
  - 172.16.31.254/19 -> địa chỉ host cuối
  - 172.16.31.255/19 -> địa chỉ broadcast
  -----
  - 172.16.32.0/19 -> địa chỉ mạng
  - 172.16.32.1/19 -> địa chỉ host đầu  
  .....  
  - 172.16.63.254/19 -> địa chỉ host cuối
  - 172.16.63.255/19 -> địa chỉ broadcast
  -----
	_....._
  -----
  - 172.16.224.0/19 -> địa chỉ mạng
  - 172.16.224.1/19 -> địa chỉ host đầu  
  .....  
  - 172.16.255.254/19 -> địa chỉ host cuối
  - 172.16.255.255/19 -> địa chỉ broadcast
- subnet mask được sử dụng là 255.255.224.0
- số prefix là 19  

__e/ 172.16.0.0/16 mượn 12 bit__   
- số bit mượn là 12, số bit mạng bây giờ là 16 + 12 = 28 
- số bit host còn lại là 32 - 28 = 4
- số subnet có thể có 2^12 = 4096
- số host trên  mỗi subnet 2^4 - 2 = 14
- địa chỉ mạng có octet thứ 4 là bội số của 16 (octet này bị mượn 4 bit)
- liệt kê các mạng như sau:
  - 172.16.0.0/28 -> địa chỉ mạng 
  - 172.16.0.1/28 -> địa chỉ host đầu  
  .....  
  - 172.16.0.14/28 -> địa chỉ host cuối
  - 172.16.0.15/28 -> địa chỉ broadcast
  -----  
  - 172.16.0.16/28 -> địa chỉ mạng
  - 172.16.0.17/28 -> địa chỉ host đầu  
	.....  
  - 172.16.0.254/28 -> địa chỉ host cuối
  - 172.16.0.255/28 -> địa chỉ broadcast
  -----  
  - 172.16.1.0/28 -> địa chỉ mạng
  - 172.16.1.1/28 -> địa chỉ host đầu  
	.....  
  - 172.16.1.254/28 -> địa chỉ host cuối
  - 172.16.1.255/28 -> địa chỉ broadcast
  -----
	_....._
  -----
  - 172.16.255.240/28 -> địa chỉ mạng
  - 172.16.255.241./28 -> địa chỉ host đầu  
  .....  
  - 172.16.255.254/28 -> địa chỉ host cuối
  - 172.16.255.255/28 -> địa chỉ broadcast  
- subnet mask được sử dụng là 255.255.255.240
- số prefix là 28  

__f/ 10.0.0.0/8 mượn 5 bit__  
- số bit mượn là 5, số bit mạng bây giờ là 5 + 8 = 13 
- số bit host còn lại là 32 - 13 = 19
- số subnet có thể có 2^5 = 32
- số host trên  mỗi subnet 2^19 - 2
- địa chỉ mạng có octet thứ 2 là bội số của 8 (octet này bị mượn 5 bit)
- liệt kê các mạng như sau:  
  - 10.0.0.0/13 -> địa chỉ mạng
  - 10.0.0.1/13 -> địa chỉ host đầu  
  .....    
  - 10.7.255.254/13 -> địa chỉ host cuối
  - 10.7.255.255/13 -> địa chỉ broadcast
  -----  
  - 10.8.0.0/13 -> địa chỉ mạng
  - 10.8.0.1/13 -> địa chỉ host đầu  
  .....  
  - 10.8.255.254/13 -> địa chỉ host cuối
  - 10.8.255.255/13 -> địa chỉ broadcast
  -----
	_....._  
	-----  
  - 10.248.0.0/13 -> địa chỉ mạng
  - 10.248.0.1/13 -> địa chỉ host đầu  
  .....  
  - 10.255.255.254/13 -> địa chỉ host cuối
  - 10.255.255.255/13 -> địa chỉ broadcast
- địa chỉ subnet mask là 255.248.0.0
- số prefix là 13  

__g/ 10.0.0.0/8 mượn 10 bit__  
- số bit mượn là 10, số bit mạng bây giờ là 10 + 8 = 18 
- số bit host còn lại là 32 - 18 = 14
- số subnet có thể có 2^10 = 1024
- số host trên  mỗi subnet 2^14 - 2
- địa chỉ mạng có octet thứ 3 là bội số của 64 (octet này bị mượn 2 bit)
- liệt kê các mạng như sau:
  - 10.0.0.0/18 -> địa chỉ mạng
  - 10.0.0.1/18 -> địa chỉ host đầu  
  .....  
  - 10.0.63.254/18 -> địa chỉ host cuối
  - 10.0.63.255/18 -> địa chỉ broadcast
  -----
	_....._  
  -----  
  - 10.0.192.0/18 -> địa chỉ mạng
  - 10.0.192.1/18 -> địa chỉ host đầu  
  .....
  - 10.0.255.254/18 -> địa chỉ host cuối
  - 10.0.255.255/18 -> địa chỉ broadcast
	-----
	_....._  
	-----  
  - 10.1.0.0/18 -> địa chỉ mạng
  - 10.1.0.1/18 -> địa chỉ host đầu  
  .....  
  - 10.1.63.254/18 -> địa chỉ host cuối
  - 10.1.63.255/18 -> địa chỉ broadcast
  -----
	_....._  
  -----  
  - 10.255.192.0/18 -> địa chỉ mạng
  - 10.255.192.1/18 -> địa chỉ host đầu  
  .....  
  - 10.255.255.254/18 -> địa chỉ host cuối
  - 10.255.255.255/18 -> địa chỉ broadcast
- địa chỉ subnet mask là 255.255.192.0
- số prefix là 18  

__h/ 10.0.0.0/8 mượn 18 bit__  
- số bit mượn là 18, số bit mạng bây giờ là 18 + 8 = 26 
- số bit host còn lại là 32 - 26 = 6
- số subnet có thể có 2^18 
- số host trên  mỗi subnet 2^6 - 2
- địa chỉ mạng có octet thứ 4 là bội số của 64 (octet này bị mượn 2 bit)
- liệt kê các mạng như sau:
  - 10.0.0.0/26 -> địa chỉ mạng
  - 10.0.0.1/26 -> địa chỉ host đầu  
  .....
  - 10.0.0.62/26 -> địa chỉ host cuối
  - 10.0.0.63/26 -> địa chỉ broadcast
  -----
  - 10.0.0.64/26 -> địa chỉ mạng
  - 10.0.0.65/26 -> địa chỉ host đầu  
  .....  
  - 10.0.0.254/26 -> địa chỉ host cuối
  - 10.0.0.255/26 -> địa chỉ broadcast
  -----  
  - 10.0.1.0/26 -> địa chỉ mạng
  - 10.0.1.1/26 -> địa chỉ host đầu  
  .....  
  - 10.0.1.254/26 -> địa chỉ host cuối
  - 10.0.1.255/26 -> địa chỉ broadcast
  -----
  _....._  
  -----  
  - 10.255.255.192/26 -> địa chỉ mạng
  - 10.255.255.193/26 -> địa chỉ host đầu  
  .....  
  - 10.255.255.254/26 -> địa chỉ host cuối
  - 10.255.255.255/26 -> địa chỉ broadcast
- địa chỉ subnet mask  là 255.255.255.192
- số prefix là 26  

> Bài tập 4.6.2  

Xét các mạng theo thứ tự số host từ cao xuống thấp. 
- Đầu tiên , xét mạng nhiều host nhất: 78 host, ta phải xem mượn bao nhiêu bit thì đủ cho mạng này.   Ta giải hệ:   
    > 2^m – 2 ≥ 79  
    m + n = 8 (mượn bit ở octet thứ 4).    

Với m: số bit host, n: số bit mượn. Ta được m = 7, n = 1. Vậy ta mượn 1 bit và dành mạng 172.16.5.0/25 để gán cho mạng có 78 host. Mỗi mạng /25 có 2^7 – 2 = 126 host => đáp ứng đủ cho mạng 78 host. 
- Tiếp đó ta xét đến mạng có 50 host, tương tự ta xem xem mượn bao nhiêu bit là phù hợp:   
    > 2^m – 2 ≥ 51   
    m + n = 8 (mượn bit ở octet thứ 4).   

Với m: số bit host, n: số bit mượn. Ta được m = 6 và n = 2 là tối ưu. Vậy ta mượn 2 bit, mạng 172.16.5.0/24 được chia thành 4 mạng 172.16.5.0/26,172.16.5.64/26, 172.16.5.128/26 và 172.16.5.192/26. Tuy nhiên hai dải địa chỉ của hai mạng 172.16.5.0/26 và 172.16.5.64/26 đã được dành cho mạng 78 host. Do đó ta chỉ có thể lấy từ mạng để gán 172.16.5.128/26 cho mạng 50 host. Ở đây ta lấy mạng 172.16.5.128/26 gán cho mạng 50 host.    
- Tiếp đó ta xét đến mạng có 20 host, ta xem xem mượn bao nhiêu bit là phù hợp: 
    > 2^m – 2 ≥ 21   
    m + n = 8 (mượn bit ở octet thứ 4). 

Với m: số bit host, n: số bit mượn. Ta được m = 5 và n = 3. Vậy ta mượn 3 bit, mạng 172.16.5.0/24 được chia thành 8 mạng 172.16.5.0/27, 172.16.5.32/27, 172.16.5.64/27 và 172.16.5.96/27, 172.16.5.128/27, 172.16.5.160/27, 172.16.5.192/27, 172.16.5.224/27 . Tuy nhiên các dải địa chỉ của các mạng 172.16.5.0/27 ,…, 172.16.5.160/27 đã được giành cho mạng 78 và mạng 50 host. Do đó ta chỉ có thể lấy từ mạng 172.16.5.192/27 trở đi để gán cho mạng 20 host. Ở đây ta lấy mạng 172.16.5.192/27 gán cho mạng 20 host. 

- Tiếp đó ta xét đến mạng có 10 host, ta xem xem mượn bao nhiêu bit là phù hợp: 
    > 2^m – 2 ≥ 11  
    m + n = 8 (mượn bit ở octet thứ 4).   

Với m: số bit host, n: số bit mượn. Ta được m = 4 và n = 4. Vậy ta mượn 4 bit, mạng 172.16.5.0/24 được chia thành 16 mạng. Ở đây ta lấy mạng 172.16.5.224/28 gán cho mạng 10 host.
- Tiếp đó ta xét đến mạng có 5 host, ta xem xem mượn bao nhiêu bit là phù hợp: 
    > 2^m – 2 ≥ 6  
    m + n = 8 (mượn bit ở octet thứ 4). 

Với m: số bit host, n: số bit mượn. Ta được m = 3 và n = 5. Vậy ta mượn 5 bit, mạng 172.16.5.0/24 được chia thành 32 mạng. Ở đây ta lấy mạng 172.16.5.240/29 gán cho mạng 5 host.
- Tiếp đó ta xét đến các mạng có 2 host là các liên kết điểm – điểm serial, ta xem thử mượn bao nhiêu bit là phù hợp: 
    > 2^m – 2 ≥ 2   
    m + n = 8 (mượn bit ở octet thứ 4).

Với m: số bit host, n: số bit mượn Ta được m = 2 và n = 6 là tối ưu hơn cả, đảm bảo không bị dư địa chỉ.. Vậy ta mượn 6 bit, mạng 172.16.5.0/24 được chia thành 2^6 = 64 mạng 172.16.5.0/30, 172.16.5.4/30, 172.16.5.8/30,…, 172.16.5.248/30, 172.16.252.0/30 . Tuy nhiên các dải địa chỉ của các mạng 172.16.5.0/30 ,…, 172.16.5.222/30 đã được giành cho mạng 78 host, mạng 50 host và mạng 20 host. Do đó ta chỉ có thể lấy từ mạng 172.16.5.248/30 để gán cho các mạng 2 host. Ở đây ta lấy mạng 172.16.5.248/30 và 172.16.5.252/30 gán cho hai liên kết serial.   
_Ta có kết quả như sau :_

![hinh_5.3](/LinhNH/04.TimhieuIpV4/images/chiamang.png)


> Bài tập 4.6.3

__a/ 192.168.1.130/29__  
/29 => có 29 bit mạng. Octet bị chia cắt là là octet thứ 4 => số bit mượn của octet này là 5 => bước nhảy là 8. Lấy octet thứ 4 của địa chỉ host là 130 chia cho 8 được 16 và còn dư. Ta lấy 16 nhân với 8 được 128. Host này thuộc mạng 192.168.1.128  
__b/ 172.16.34.57/18__   
/18 => có 18 bit mạng. Octet bị chia cắt là octet thứ 3 => số bit mượn của octet này là 2 => bước nhảy là 64. Lấy octet thứ 4 của địa chỉ host là 34 chia cho 64 được 0. Ta lấy 0 nhân với 64 được 0. Host này thuộc mạng 172.16.0.57  
__c/ 203.162.4.191/28__  
/28 => có 28 bit mạng. Octet bị chia cắt là octet thứ 4 => số bit mượn của octet này là 4 => bước nhảy là 16. Lấy octet thứ 4 của địa chỉ host là 191 chia cho 16 được 11 dư 15. Ta lấy 11 nhân với 16 được 176. Host này thuộc mạng 203.162.4.176  
__d/ 1.1.1.1/30__   
/30 => có 30 bit mạng. Octet bị chia cắt là octet thứ 4 => số bit mượn của octet này là 6 => bước nhảy là 4. Lấy octet thứ 4 của địa chỉ host là 1 chia cho 4 được 0. Ta lấy 0 nhân với 4 được 0. Host này thuộc mạng 1.1.1.0  
__e/ 10.10.10.89/29__  
/29 => có 29 bit mạng. Octet bị chia cắt là octet thứ 4 => số bit mượn của octet này là 5 => bước nhảy là 8. Lấy octet thứ 4 của địa chỉ host là 89 chia cho 8 được 11 dư 1. Ta lấy 11 nhân với 8 được 88. Host này thuộc mạng 10.10.10.88   
__f/ 70.9.12.35/30__  
/30 => có 30 bit mạng. Octet bị chia cắt là octet thứ 4 => số bit mượn của octet này là 6 => bước nhảy là 4. Lấy octet thứ 4 của địa chỉ host là 35 chia cho 4 được 8 dư 3. Ta lấy 8 nhân với 4 được 32. Host này thuộc mạng 70.9.12.32  
__g/ 158.16.23.208/29__
/29 => có 29 bit mạng. Octet bị chia cắt là octet thứ 4 => số bit mượn của octet này là 5 => bước nhảy là 8. Lấy octet thứ 4 của địa chỉ host là 208 chia cho 8 được 26. Ta lấy 26 nhân với 8 được 208. Host này thuộc mạng 158.16.23.208  
> Bài tập 4.6.4  

__a/__   	  
  192.168.0.0/24  
	192.168.1.0/24  
	192.168.2.0/24  
	192.168.3.0/24  
Trong các mạng trên, octet thứ 3 là octet khác nhau đầu tiên, ta xét chi tiết octet này:  
192.168.{000000|00}.0  
192.168.{000000|01}.0  
192.168.{000000|10}.0  
192.168.{000000|11}.0  
Ta thấy octet thứ 3 có 6 bit 0 giống nhau. Vậy ta có mạng tóm tắt là 192.168.0.0/22  
__b/__	  
  172.16.16.0/24  
	172.16.20.0/24  
	172.16.24.0/24  
	172.16.28.0/24  
Trong các mạng trên, octet thứ 3 là octet khác nhau đầu tiên, ta xét chi tiết octet này:  
172.16.{0001|0000}.0  
172.16.{0001|0100}.0  
172.16.{0001|1000}.0  
172.16.{0001|1100}.0  
Ta thấy octet thứ 3 có 4 bit (3 bit 0, 1 bit 1) giống nhau. Vậy ta có mạng tóm tắt là 172.16.0.0/20






