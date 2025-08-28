# .01 NAT là gì?
NAT (Network Address Translation) là cơ chế dịch địa chỉ mạng được sử dụng trong các thiết bị mạng (thường là router hoặc firewall) để chuyển đổi địa chỉ IP riêng (private IP) trong mạng LAN thành địa chỉ IP công cộng (public IP) khi truy cập Internet, và ngược lại.

![alt text](1.jpg)
**Mục đích của NAT**

- 1.Chia sẻ kết nối Internet
Cho phép nhiều máy trong mạng LAN (dùng IP private) cùng truy cập Internet thông qua một hoặc một vài địa chỉ IP public.
Giúp tiết kiệm tài nguyên địa chỉ IPv4 vốn đang khan hiếm.

- 2. Ẩn địa chỉ mạng nội bộ (Bảo mật)
Các máy trong LAN chỉ hiện ra ngoài Internet dưới dạng địa chỉ public của NAT.
Hacker từ Internet khó biết được cấu trúc thật sự của mạng nội bộ.

- 3. Tiết kiệm và quản lý địa chỉ IPv4
NAT cho phép hàng trăm hoặc hàng nghìn máy trong LAN dùng chung 1 IP public.
Giảm bớt nhu cầu đăng ký nhiều địa chỉ IPv4 với nhà cung cấp dịch vụ.

- 4. Kết nối các mạng có địa chỉ trùng lặp
Khi hai công ty sát nhập hoặc khi có nhiều mạng dùng cùng dải IP private, NAT giúp “dịch” địa chỉ để chúng vẫn có thể giao tiếp.

- 5. Cho phép truy cập dịch vụ nội bộ từ bên ngoài (Static NAT / Port Forwarding)

Ví dụ: Công ty có Web Server nội bộ đặt tại LAN (IP: 192.168.1.100).
NAT ánh xạ (map) địa chỉ public (203.113.x.x) tới máy chủ đó, để người ngoài có thể truy cập.


## .2 Phân loại NAT
1. Static NAT (NAT tĩnh)

Cách hoạt động:

- Ánh xạ một địa chỉ private ↔ một địa chỉ public cố định.
- Mối quan hệ này không thay đổi (tĩnh).
Ứng dụng:
- Dùng cho server nội bộ (web, mail, FTP...) cần được truy cập từ Internet.

- Ví dụ:
192.168.1.10 ↔ 203.113.5.10

🔹 2. Dynamic NAT (NAT động)
Cách hoạt động:

- Sử dụng một pool (nhóm) địa chỉ public.
- Khi một máy trong LAN cần ra Internet, router sẽ chọn ngẫu nhiên một IP public trong pool để ánh xạ.
- Hết phiên thì giải phóng IP đó.

Ứng dụng:
- Mạng lớn, có sẵn nhiều IP public và muốn phân phát linh hoạt.

Ví dụ:
- Pool public: 203.113.5.20 – 203.113.5.30
- Máy 192.168.1.15 có thể được dịch thành 203.113.5.22 trong phiên làm việc.

🔹 3. PAT (Port Address Translation)
Còn gọi là NAT Overload.

Cách hoạt động:
- Nhiều máy trong LAN cùng dùng chung 1 địa chỉ public, nhưng phân biệt nhau bằng số port.
- Router sẽ thay đổi cả IP và port nguồn khi gửi ra ngoài.

Ứng dụng:
- Phổ biến nhất hiện nay (hầu hết các hộ gia đình và công ty nhỏ dùng).

Ví dụ:
Máy 192.168.1.10 gửi ra → 203.113.5.20:30001
Máy 192.168.1.11 gửi ra → 203.113.5.20:30002

| Loại NAT               | Đặc điểm                                | Ưu điểm                        | Nhược điểm                         | Ứng dụng                            |
| ---------------------- | --------------------------------------- | ------------------------------ | ---------------------------------- | ----------------------------------- |
| **Static NAT**         | 1 private ↔ 1 public (cố định)          | Dễ quản lý, phù hợp cho server | Tốn nhiều địa chỉ public           | Server nội bộ cần truy cập từ ngoài |
| **Dynamic NAT**        | 1 private ↔ 1 public (tạm thời từ pool) | Linh hoạt                      | Cần nhiều địa chỉ public           | Mạng lớn có nhiều IP public         |
| **PAT (NAT Overload)** | Nhiều private ↔ 1 public (dùng port)    | Tiết kiệm IP nhất, phổ biến    | Có thể gây nghẽn nếu nhiều kết nối | Gia đình, doanh nghiệp nhỏ          |

### .3 Cơ chế hoạt động của NAT
1. Nguyên lý cơ bản
- NAT nằm trên router/firewall kết nối LAN ↔ Internet.

Khi gói tin đi ra ngoài:
- NAT sẽ thay đổi địa chỉ IP nguồn (Source IP) từ private IP → public IP.
- Nếu là PAT, nó còn thay đổi cả port nguồn (Source Port).

Khi gói tin trả về từ Internet:
- NAT sẽ dịch ngược lại từ public IP (và port) → private IP để gửi về đúng thiết bị trong LAN.

2. Cơ chế hoạt động chi tiết



![alt text](<Ảnh màn hình 2025-08-28 lúc 14.28.28.png>)


#### 4. Hạn chế của NAT là gì?



**Hạn chế**

Mặc dù NAT có những lợi ích đáng kể trong việc kết nối những thiết bị trong mạng cục bộ đến Internet và những mạng khác, nó cũng có một số hạn chế và rủi ro tiềm ẩn như dưới đây.

- Giới hạn số lượng kết nối: NAT giới hạn số lượng kết nối mà một địa chỉ IP có thể mở đồng thời. Điều này có thể gây ra những vấn đề cho những ứng dụng đòi hỏi số lượng kết nối lớn như những ứng dụng P2P, game trực tuyến hay những trang web phục vụ nhiều người dùng cùng lúc.
- Hạn chế về độ trễ và tốc độ: NAT có thể làm giảm tốc độ mạng do các gói tin phải trải qua quá trình chuyển đổi địa chỉ IP. Việc này có thể gây ra độ trễ cao và giảm hiệu suất mạng.
- Khó khăn trong việc xác định kết nối: NAT khiến cho việc xác định kết nối trở nên khó khăn, đặc biệt là khi kết nối được thiết lập thông qua nhiều tường lửa và router. Điều này có thể gây ra những vấn đề khi gỡ lỗi mạng hay khi cấu hình những thiết bị mạng.
- Vấn đề liên quan đến bảo mật: Một số cuộc tấn công từ bên trong mạng có thể vượt qua NAT và gây ra những vấn đề bảo mật cho nhiều thiết bị trong mạng.
- Vấn đề tương thích: NAT có thể gây ra những vấn đề về tương thích khi kết nối những thiết bị trong mạng cục bộ đến những dịch vụ trực tuyến hoặc khi sử dụng những ứng dụng đòi hỏi địa chỉ IP duy nhất như VoIP hay game trực tuyến. Khi NAT được sử dụng, nhiều thiết bị trong mạng cục bộ sẽ sử dụng cùng một địa chỉ IP công cộng. Điều này có thể gây ra sự cố khi những thiết bị này đang cố gắng truy cập cùng một dịch vụ trực tuyến đòi hỏi địa chỉ IP riêng.

tham khảo:

https://fptshop.com.vn/tin-tuc/danh-gia/nat-la-gi-157684

https://waren.vn/chuyen-de/nat-ly-thuyet-tong-quan.html


