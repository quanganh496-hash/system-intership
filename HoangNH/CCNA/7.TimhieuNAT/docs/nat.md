# Tìm hiều về NAT

## 1.Giới thiệu về NAT

NAT - Network Address Translation - chuyển đổi địa chỉ mạng là một kỹ thuật cho phép các thiết bị trong mạng riêng của bạn (private network) truy cập vào Internet thông qua một địa chỉ IP công cộng duy nhất. Khi các thiết bị trong mạng riêng gửi yêu cầu tới Internet, địa chỉ IP công cộng sẽ được sử dụng để giao tiếp với các máy chủ trên Internet.

![image1](/HoangNH/7.TimhieuNAT/image/nat.png)

### 2.Phân loại NAT

### 2.1.Static NAT

Static NAT là một phương pháp NAT mà cho phép ánh xạ một địa chỉ IP tĩnh (công cộng) tới một địa chỉ IP tĩnh (riêng) cụ thể trên mạng nội bộ.

Khi sử dụng Static NAT, địa chỉ IP công cộng được cấu hình trên router hoặc firewall để được ánh xạ tới địa chỉ IP riêng của thiết bị trên mạng nội bộ. Điều này cho phép thiết bị trong mạng nội bộ có thể được truy cập từ mạng bên ngoài với địa chỉ IP công cộng được cấu hình.

Một số ứng dụng của Static NAT bao gồm:

- Cho phép các máy chủ trong mạng nội bộ được truy cập từ mạng bên ngoài với địa chỉ IP công cộng.
- Cho phép các ứng dụng yêu cầu địa chỉ IP tĩnh được hoạt động trên mạng nội bộ.
- Cung cấp tính bảo mật cao hơn bằng cách ẩn địa chỉ IP thực của các thiết bị trong mạng nội bộ khỏi mạng bên ngoài.

Ví dụ: Máy tính trong mạng nội bộ có địa chỉ IP là 192.168.1.10 muốn truy cập một trang web bên ngoài internet.
Khi gói tin từ máy tính này đi qua thiết bị NAT, địa chỉ IP nguồn sẽ được thay đổi thành địa chỉ IP công cộng của thiết bị NAT, ví dụ 203.0.113.5.
Trang web nhận được yêu cầu từ địa chỉ IP 203.0.113.5 và gửi phản hồi lại cho địa chỉ này.
Thiết bị NAT nhận được phản hồi và dịch ngược địa chỉ IP nguồn từ 203.0.113.5 thành 192.168.1.10 để gửi lại cho máy tính trong mạng nội bộ.

![image2](/HoangNH/7.TimhieuNAT/image/staticnat.webp)

### 2.2.Dynamic NAT

Dynamic NAT là một phương pháp NAT mà cho phép các địa chỉ IP tĩnh được ánh xạ tới các địa chỉ IP công cộng tạm thời theo yêu cầu.

Khi sử dụng Dynamic NAT, một bộ đệm địa chỉ IP công cộng được cấu hình trên router hoặc firewall để phục vụ việc ánh xạ địa chỉ IP. Khi một thiết bị trong mạng nội bộ yêu cầu truy cập mạng bên ngoài, router sẽ chọn một địa chỉ IP công cộng tạm thời từ bộ đệm địa chỉ IP và ánh xạ nó tới địa chỉ IP tĩnh của thiết bị trong mạng nội bộ. Sau khi kết thúc phiên làm việc, địa chỉ IP công cộng tạm thời sẽ được trả về vào bộ đệm để tái sử dụng.

Một số ứng dụng của Dynamic NAT bao gồm:

- Giúp tăng tính bảo mật bằng cách ẩn địa chỉ IP thực của các thiết bị trong mạng nội bộ khỏi mạng bên ngoài.
- Giúp tiết kiệm địa chỉ IP công cộng bằng cách sử dụng chúng tạm thời thay vì cấp phát địa chỉ IP tĩnh cho mỗi thiết bị trong mạng nội bộ.
- Cho phép nhiều thiết bị trong mạng nội bộ sử dụng chung một địa chỉ IP công cộng.

Ví dụ: Trong hệ thống LAN của công ty có 100 IP, việc sử dụng NAT tĩnh đòi hỏi phải thuê 100 IP Public từ ISP. Vì vậy sử dụng NAT động giúp giảm chi phí bằng cách chỉ cần thuê 10 IP Public từ ISP nếu thời điểm đó có 10 IP truy cập internet.
Nếu có 20 IP muốn truy cập thì phải chờ 10 IP kia truy cập xong mới được sử dụng. 

![image3](/HoangNH/7.TimhieuNAT/image/dynamicnat.webp)

### 2.3.NAT Overload

NAT Overload, còn được gọi là Port Address Translation (PAT), là một dạng của NAT mà cho phép nhiều địa chỉ IP tĩnh trong mạng nội bộ được ánh xạ tới một địa chỉ IP công cộng duy nhất bằng cách sử dụng các cổng khác nhau.

Khi một thiết bị trong mạng nội bộ yêu cầu truy cập mạng bên ngoài, router NAT sẽ ánh xạ địa chỉ IP và số cổng của thiết bị nội bộ tới một địa chỉ IP và một số cổng khác nhau trên địa chỉ IP công cộng. Các cổng này được sử dụng để phân biệt các kết nối khác nhau của các thiết bị nội bộ trên cùng một địa chỉ IP công cộng.

Một số ưu điểm của NAT Overload bao gồm:

- Giúp tiết kiệm địa chỉ IP công cộng bằng cách sử dụng cùng một địa chỉ IP công cộng cho nhiều thiết bị trong mạng nội bộ.
- Giúp tăng tính bảo mật bằng cách ẩn địa chỉ IP thực của các thiết bị trong mạng nội bộ khỏi mạng bên ngoài.
- Cho phép nhiều thiết bị trong mạng nội bộ sử dụng cùng lúc một địa chỉ IP công cộng để truy cập mạng bên ngoài.

![image4](/HoangNH/7.TimhieuNAT/image/pat.webp)

Ví dụ: Trong mạng nội bộ, máy A có địa chỉ 192.168.1.10, máy B có địa chỉ 192.168.1.20, máy A muốn truy cập 1 trang web, máy B muốn gửi mail đến máy chủ trên internet, hai máy tính gửi yêu cầu đến cùng một địa chỉ IP công cộng của thiết bị NAT, ví dụ 203.0.113.5.
nhưng sẽ qua các cổng khác nhau, máy A qua cổng 80, máy B qua cổng 25.
Thiết bị NAT lưu lại thông tin về cả địa chỉ IP và cổng của mỗi kết nối. Các trang web từ internet sẽ phản hồi lại qua các cổng khác nhau. 
NAT sử dụng thông tin về cổng để xác định nội dung phản hồi nào thuộc về máy A và nội dung nào thuộc về máy B, và gửi chúng đến đúng máy tương ứng. 

### 2.4.SNAT

SNAT (Source Network Address Translation) thường được sử dụng khi máy chủ nội bộ/private cần bắt đầu kết nối với máy chủ bên ngoài/public. Thiết bị thực hiện NAT thay đổi địa chỉ IP riêng của máy chủ nguồn thành IP Public. Nó cũng có thể thay đổi cổng nguồn trong TCP/ UDP.

Một tình huống điển hình của SNAT là khi được yêu cầu thay đổi địa chỉ hay cổng riêng thành public khi các gói rời khỏi mạng. Về thứ tự hoạt động, SNAT xuất hiện sau khi quyết định định tuyến được đưa ra. Bên cạnh đó, khi có nhiều máy chủ trên mạng “bên trong” muốn truy cập vào “bên ngoài”, SNAT sẽ được sử dụng.

![image5](/HoangNH/7.TimhieuNAT/image/snat.gif)

### 2.5.DNAT

DNAT (Destination Network Address Translation) có chức năng thay đổi địa chỉ đích trong IP của gói tin.

Ngoài ra, DNAT cũng có thể thay đổi cổng đích trong TCP / UDP. Ứng dụng điển hình của nó là chuyển hướng các gói đến với đích là một địa chỉ/ cổng public, đi đến một địa chỉ/ cổng IP private bên trong mạng.

Người dùng qua internet truy cập máy chủ web được lưu trữ trong trung tâm dữ liệu là một ví dụ điển hình mà DNAT được sử dụng để ẩn địa chỉ private. Đồng thời, thiết bị NAT chuyển IP đích public mà người dùng internet có thể truy cập thành địa chỉ IP private của máy chủ web.

![image6](/HoangNH/7.TimhieuNAT/image/dnat.gif)

|  | SNAT | DNAT |
|:--|:----|:----|
|Thuật ngữ| đổi địa chỉ IP riêng của máy chủ nguồn thành IP Public| đổi địa chỉ đích trong IP của gói tin|
|Trường hợp sử dụng| Khi một client bên trong mạng LAN hay sau firewall muốn sử dụng internet| Khi một website được lưu trữ bên trong trung tâm dữ liệu, sau firewall cần cho người dùng bên ngoài (public) kết nối đến thông qua mạng|
|Thứ tự hoạt động| sau khi thực hiện định tuyến | trước khi thực hiện định tuyến |
|Thay đổi địa chỉ | thay đổi địa chỉ nguồn của gói đi qua thiết bị NAT| thay đổi địa chỉ đích của gói đi qua Router|
|Đơn/đa máy chủ| cho phép nhiều máy chủ bên trong mạng truy cập vào bất ký máy chủ nào bên ngoài| cho phép máy chủ bên ngoài truy cập vào một máy chủ bên trong|

### 3.Cơ chế hoạt động

NAT sử dụng IP của chính nó làm IP công cộng cho mỗi máy con (client) với IP riêng. Khi một máy con thực hiện kết nối hoặc gửi dữ liệu tới một máy tính nào đó trên Internet, dữ liệu sẽ được gửi tới NAT, sau đó NAT sẽ thay thế địa chỉ IP gốc của máy con đó rồi gửi gói dữ liệu đi với địa chỉ IP của NAT. Máy tính từ xa hoặc máy tính nào đó trên Internet khi nhận được tín hiệu sẽ gửi gói tin trở về cho NAT computer bởi chúng nghĩ rằng NAT computer là máy đã gửi những gói dữ liệu đi. NAT ghi lại bảng thông tin của những máy tính đã gửi những gói thông tin ra ngoài trên mỗi cổng dịch vụ và gửi những gói tin nhận được về đúng client đó.

NAT xử lý một gói tin xuất phát từ bên trong đi ra bên ngoài một mạng theo cách thức sau:

- tiến trình NAT tìm kiếm một hàng ở trong bảng NAT trong đó địa chỉ outside local address bằng với địa chỉ đích của gói tin. Nếu không có phép so sánh trùng nào được tìm thấy, gói tin đó sẽ bị loại bỏ.
- nếu bằng, NAT sẽ thay thế địa chỉ đích trong gói tin bằng địa chỉ outside global theo thông tin trong bảng NAT.
- Tiến trình NAT tiếp tục tìm kiếm bảng NAT để xem có một địa chỉ Inside local nào bằng với địa chỉ nguồn của gói tin hay không. 
- Nếu có một hàng là tìm thấy, NAT tiếp tục thay thế địa chỉ nguồn của gói tin bằng địa chỉ Inside global. 
- Nếu không có một hàng nào được tìm thấy, NAT sẽ tạo ra một hàng mới trong bảng NAT và chèn địa chỉ mới vào trong gói tin.
- Router tìm kiếm bảng NAT để tìm ra địa chỉ Outside global bằng với địa chỉ nguồn của gói tin. 
- Nếu có một hàng là tìm thấy, NAT sẽ thay thế địa chỉ đích bằng địa Outside local từ bảng NAT. 
- Nếu NAT không tìm thấy một hàng nào, nó sẽ tạo ra một hàng mới trong bảng NAT và chèn địa chỉ mới vào trong gói tin.

 