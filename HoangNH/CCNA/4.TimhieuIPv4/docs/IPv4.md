# Tìm hiểu về IPv4

## 1.IPv4 là gì?

IPv4 là một giao thức mạng Internet dựa trên việc sử dụng địa chỉ IP để xác định vị trí của các thiết bị trong mạng.

IPv4 đã được sử dụng trong hơn 30 năm và vẫn là giao thức mạng phổ biến nhất trên toàn thế giới. Tuy nhiên, IPv4 đang dần bị thay thế bởi IPv6, vì các giới hạn về địa chỉ IP của nó.

IPv4 là giao thức hướng dữ liệu, được sử dụng cho hệ thống chuyển mạch gói (tương tự như chuẩn mạng Ethernet). Đây là giao thức truyền dữ liêu hoạt động dựa trên nguyên tắc tốt nhất có thể, trong đó, nó không quan tâm đến thứ tự truyền gói tin cũng như không đảm bảo gói tin sẽ đến đích hay việc gây ra tình trạng lặp gói tin ở đích đến. Việc xử lý vấn đề này dành cho lớp trên của chồng giao thức TCP/IP. Tuy nhiên, IPv4 có cơ chế đảm bảo tính toàn vẹn dữ liệu thông qua sử dụng những gói kiểm tra (checksum).

Ipv4 là giao thức mang tính hướng dữ liệu và được sử dụng cho hệ thống chuyển mạch gói. Ipv4 không quan tâm đến thứ tự truyền gói tin, cũng không đảm bảo gói tin sẽ đến đích hay là có xảy ra tình trạng lặp gói tin ở đích đến hay không. Nó chỉ có cơ chế đảm bảo tính toàn vẹn dữ liệu bằng việc sử dụng những gói kiểm tra được thiết lập đi kèm với nó.

## 2.Tại sao không có IPv1,2,3,5

Trước khi IP ra đời như chúng ta biết ngày nay, các kiến ​​trúc sư mạng đã làm việc trên TCP. TCPv1 được thiết kế vào năm 1973, TCPv2 được ghi lại vào tháng 3 năm 1977.
Hai phiên bản này phục vụ như một giao thức đầu cuối cấp máy chủ và để phục vụ như một giao thức định tuyến và đóng gói internet.
Sau đó phiên bản thứ ba được triển khai xong vẫn chưa giải quyết được vấn đề ban đầu.

IPv5 chưa bao giờ trở thành một giao thức chính thức. Với sự phát triển của IPv6, IPv5 không bao giờ được chuyển sang sử dụng công cộng phần lớn vì những hạn chế 32-bit của nó. Với sự phát triển của IPv6 và lời hứa của nó về địa chỉ IP gần như không giới hạn và một khởi đầu mới cho giao thức, IPv5 không bao giờ được chuyển sang sử dụng công cộng phần lớn vì những hạn chế 32-bit của nó.Định dạng của địa chỉ IPv4 là định dạng ###. ###. ###. ###, được tạo thành từ bốn bộ tám số (một đơn vị thông tin kỹ thuật số trong máy tính bao gồm tám bit), với mỗi bộ khác nhau từ 0 đến 255 và được phân tách bằng dấu chấm. Định dạng này cho phép 4,3 tỷ địa chỉ internet; tuy nhiên, tốc độ phát triển nhanh chóng của Internet đã sớm làm cạn kiệt số lượng địa chỉ duy nhất này.
Đến năm 2011, các khối địa chỉ IPv4 còn lại cuối cùng đã được cấp phát. Với IPv5 sử dụng cùng một địa chỉ 32-bit, nó sẽ bị hạn chế tương tự.

## 3.Cấu trúc của IPv4

Địa chỉ IPv4 sẽ có 32 bit và được biểu diễn thành một dãy số nhị phân và chia thành 4 cụm. Mỗi cụm như vậy sẽ gọi là octet. Mỗi octet sẽ là 8 bit và chúng được ngăn cách bằng dấu chấm (.)

Về hình dáng, cấu trúc của một địa chỉ IPv4 sẽ gồm 4 con số ở dạng thập phân tượng trưng cho 4 cụm. 

![image1](/HoangNH/4.TimhieuIPv4/image/cautruc.jpg)

## 4.Các thành phần của IPv4

Địa chỉ IP gồm 2 phần là phần network và phần host.

Phần network chính là địa chỉ cho chính network đó.Phần host dành để đánh cho cách thiết bị mạng ở trong network đó

## 5.Các lớp của IPv4

Dựa vào cách chọn địa chỉ mạng mà địa chỉ IP được phân thành 5 lớp A, B, C, D, E.

### 5.1.Lớp A

![image2](/HoangNH/4.TimhieuIPv4/image/A.jpg)

Địa chỉ lớp A có phần mạng là 8 bit đầu và phần host là 24 bit sau. Bit đầu tiên của phần mạng luôn là 0.

Lớp A sẽ có các địa chỉ mạng từ 1.0.0.0 đến 126.0.0.0 và mỗi mạng sẽ có 224 địa chỉ host (loại trừ địa chỉ mạng và địa chỉ broadcast).

Mạng loopback sẽ là 127.0.0.0.

### 5.2.Lớp B

![image3](/HoangNH/4.TimhieuIPv4/image/B.jpg)

Địa chỉ lớp B có phần mạng là 16 bit đầu và phần host là 16 bit sau. 2 bit đầu tiên của phần mạng luôn là 1.0.

Lớp B sẽ có các địa chỉ mạng từ 128.0.0.0 đến 191.255.0.0 và mỗi mạng sẽ có 214 địa chỉ host (loại trừ địa chỉ mạng và địa chỉ broadcast).

### 5.3.Lớp C

![image4](/HoangNH/4.TimhieuIPv4/image/C.jpg)

Địa chỉ lớp C có phần mạng là 24 bit đầu và phần host là 8 bit sau. 3 bit đầu tiên của phần mạng luôn là 1.1.0.

Lớp C sẽ có các địa chỉ mạng từ 192.0.0.0 đến 223.255.255.0 và mỗi mạng sẽ có 26 địa chỉ host (loại trừ địa chỉ mạng và địa chỉ broadcast).

### 5.4.Lớp D

Các địa chỉ trong lớp D là những địa chỉ multicast bao gồm 224.0.0.0 đến 239.255.255.255.

### 5.5.Lớp E

Các địa chỉ trong lớp E có vai trò dùng để dự phòng, bao gồm những địa chỉ từ 240.0.0.0 trở đi.

## 6.Phân biệt IP public và IP private

### 6.1.IP public

IP public là địa chỉ duy nhất được gán cho các thiết bị kết nối với Internet. IP public cho phép các thiết bị truy cập vào các dịch vụ trên mạng và giao tiếp với các máy chủ khác trên toàn thế giới.

IP public được nhà cung cấp dịch vụ Internet (ISP) dùng để chuyển tiếp các yêu cầu Internet đến các gia đình hoặc doanh nghiệp cụ thể.

![image5](/HoangNH/4.TimhieuIPv4/image/public.jpg)

IP public đóng vai trò quan trọng trong việc truy cập Internet và giao tiếp trực tuyến. Nó cho phép các thiết bị truy cập vào các trang web, gửi hoặc nhận dữ liệu từ các máy chủ và tham gia vào các hoạt động trực tuyến khác.

### 6.2.IP private:

IP private là địa chỉ IP chỉ sử dụng trong mạng nội bộ và không được sử dụng để truy cập Internet trực tiếp.

IP Private thường được sử dụng trong các mạng nội bộ như: mạng gia đình, doanh nghiệp, tổ chức, công ty, trường học,.. để phân bổ địa chỉ IP cho các thiết bị trên mạng trong phạm vi cục bộ.

![image6](/HoangNH/4.TimhieuIPv4/image/private.png)

Phạm vi của IP private:

- 10.0.0.0 đến 10.255.255.255
- 172.16.0.0 đến 172.31.255.255
- 192.168.0.0 đến 192.168.255.255

Bảng so sánh: 

| Tiêu chí |  IP public | IP private |
|:------|:-----------------|:------|
|Hoạt động| Hệ thống mạng toàn cầu | Hệ thống mạng cục bộ |
|Nguồn gốc | Được chỉ định bởi ISP | Được chỉ định bởi bộ định tuyến cho một thiết bị cụ thể trên mạng cục bộ|
|Liên lạc| Dùng để giao tiếp qua Internet | Được sử dụng để liên lạc trong một mạng riêng|
|Quy tắc | Địa chỉ IP Public có thể hoạt động khác nhau theo một quy luật đồng nhất hay không đồng nhất | Địa chỉ IP Private sẽ được kết nối khác nhau trong mạng, nhưng vẫn tuân thủ theo một quy luật thống nhất |
|Phạm vi| Trừ một số địa chỉ nằm trong IP Private, phần còn lại sẽ là IP Public| 10.0.0.0 đến 10.255.255.255 / 172.16.0.0 đến 172.31.255.255 / 192.168.0.0 đến 192.168.255.255 |
                           


## 8.Phân biệt multicast và broadcast

### 8.1.Multicast

Multicast là một kiểu truyền tải dữ liệu trên mạng mà cho phép một thiết bị hoặc máy chủ gửi một tin nhắn hoặc dữ liệu tới nhiều thiết bị hoặc máy chủ khác cùng một lúc.

![image7](/HoangNH/4.TimhieuIPv4/image/multicast.jpg)

Multicast sẽ được bắt đầu từ Server đảm nhiệm vai trò gửi gói tin dữ liệu cho hàng loạt người nhận khác nhau. Thiết bị nhận bắt buộc phải sử dụng địa chỉ IP nằm trong vùng IP được thiết kế cho việc lưu thông Multicast. Nó dao động từ 224.0.0.0 cho đến 239.255.255.255.

Sau khi Router nhận được dữ liệu lưu thông từ Multicast, nó sẽ cần đến giao thức IGMP (Internet Group Management Protocol) để xác định xem đâu là thiết bị kết nối nguồn nhận dữ liệu. Giao thức IGMP được hiểu là giao thức giao tiếp cho thiết bị mạng tạo ra nhóm Multicast.

### 8.2.Broadcast

Broadcast là một khái niệm trong mạng máy tính và hệ thống mạng. Địa chỉ broadcast là một địa chỉ IP đặc biệt dùng để gửi các gói tin tới tất cả các máy trong một mạng có cùng dải mạng. Ví dụ, nếu một máy tính có địa chỉ IP là 192.168.1.10 và có dải mạng là 255.255.255.0, thì địa chỉ broadcast của nó sẽ là 192.168.1.255. Một gói tin gửi đi tới địa chỉ broadcast sẽ được chuyển tiếp tới tất cả các máy trong mạng có cùng dải mạng.

Địa chỉ broadcast cũng có thể được dùng để thực hiện các tác vụ khác trong mạng, như việc tìm kiếm các thiết bị khác trong mạng, hoặc cung cấp các dịch vụ đặc biệt cho các máy trong mạng.

![image8](/HoangNH/4.TimhieuIPv4/image/broadcast.png)

Bảng so sánh: 

| Tiêu chí |  multicast | broadcast |
|:------   |:-----------------|:------ |
|Định nghĩa| Một nguồn độc lập sẽ gửi một dữ liệu giống nhau cho hàng loạt người nhận ở cùng một thời điểm|Một nguồn độc lập gửi dữ liệu cho tất cả đích đến.|
|Cách thức tương tác| Tương tác diễn ra giữa một người gửi và rất nhiều người nhận cùng lúc.| Tương tác diễn ra giữa một người gửi và tất cả người nhận khả dụng.|
|Cách thức hoạt động|Dữ liệu được luân chuyển khi nhận yêu cầu từ những người nhận cùng lúc.|Dữ liệu được luân chuyển cho tất cả người nhận bất kể có nhận được yêu cầu hay không.|
|Độ bảo mật| Có độ bảo mật cao vì dữ liệu được gửi đến một nhóm người nhận nhất định| Độ bảo mật thấp do dữ liệu được gửi đến tất cả thiết bị trong mạng lưới|
|Độ trễ| Trung bình| Cao|
## 9.Subnet, subnet mask, prefix

### 9.1.Subnet:

Subnet (hay còn gọi là mạng con) là một phần của một mạng lớn được chia nhỏ để quản lý tài nguyên mạng hiệu quả hơn. Một subnet được định nghĩa bởi một địa chỉ IP mạng và một subnet mask. Các thiết bị trong cùng một subnet có thể giao tiếp với nhau trực tiếp mà không cần thông qua một router.

### 9.2.Subnet mask:

Subnet mask là một dải 32 bit nhị phân đi kèm với một địa chỉ IP, được các host sử dụng để xác định địa chỉ mạng của địa chỉ IP này.

### 9.3.Prefix

Để mô tả một địa chỉ IP, người ta dùng một đại lượng khác được gọi là số prefix. Số prefix có thể hiểu một cách đơn giản là số bit mạng trong một địa chỉ IP, được viết ngay sau địa chỉ IP, và được ngăn cách với địa chỉ này bằng một dấu “/”.

Ví du: 192.168.1.1/24, 172.16.0.0/16 hay 10.0.0.0/8, v.v…

