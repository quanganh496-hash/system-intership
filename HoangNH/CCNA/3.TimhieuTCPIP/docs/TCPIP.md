# Tìm hiểu về TCP/IP


## 1.Giới thiệu về TCP/IP

TCP/IP (Transmission Control Protocol/ Internet Protocol – Giao thức điều khiển truyền nhận/ Giao thức liên mạng), là một bộ giao thức trao đổi thông tin được sử dụng để truyền tải và kết nối các thiết bị trong mạng Internet. TCP/IP được phát triển để mạng được tin cậy hơn cùng với khả năng phục hồi tự động.

TCP/IP gồm hai phần chính:

- Transmission Control Protocol (TCP): Là một giao thức truyền tải đáng tin cậy được sử dụng để chia nhỏ và lắp ráp các gói dữ liệu trước khi chúng được gửi qua mạng. TCP đảm bảo rằng các gói dữ liệu được gửi đi sẽ đến đích một cách chính xác và đúng thứ tự. Nó xác định các kết nối, đồng bộ hóa truyền tải và quản lý lưu lượng dữ liệu.
- Internet Protocol (IP): Là một giao thức định tuyến và chuyển tiếp dữ liệu trong mạng. IP định danh và địa chỉ hóa các thiết bị trong mạng, đồng thời quản lý việc định tuyến (routing) các gói dữ liệu qua mạng. Giao thức này đảm bảo gói dữ liệu được gửi đến đúng đích và định vị các thiết bị trong mạng.

## 2.Các tầng trong TCP/IP

Mô hình TCP/IP gồm 4 tầng.


![image1](/HoangNH/3.TimhieuTCPIP/image/image1.png)


### 2.1.Tầng vật lý

Là tầng thấp nhất trong mô hình TCP/IP.Nó là sự kết hợp của tầng vật lý và liên kết dữ liệu trong mô hình OSI.

Tầng này chịu trách nhiệm truyền dữ liệu giữa các thiết bị trong cùng một mạng. Tại đây, các gói dữ liệu được đóng vào khung (Frame) và được định tuyến đi đến đích được chỉ định ban đầu.

### 2.2.Tầng mạng

Là tầng thứ hai trong mô hình TCP/IP. Tầng này chịu trách nhiệm truyền tải dữ liệu một cách logic trong mạng. 

Các phân đoạn dữ liệu sẽ được đóng gói (Packets) với kích thước mỗi gói phù hợp với mạng chuyển mạch mà nó dùng để truyền dữ liệu. Lúc này, các gói tin được chèn thêm phần Header chứa thông tin của tầng mạng và tiếp tục được chuyển đến tầng tiếp theo. 

Các giao thức chính trong tầng là IP, ICMP và ARP.


### 2.3.Tầng giao vận

Là tầng thứ ba trong mô hình TCP/IP. Tầng này chịu trách nhiệm duy trì liên lạc đầu cuối trên toàn mạng.

Tầng này có 2 giao thức chính:

- TCP (Transmission Control Protocol) cung cấp luồng dữ liệu tin cậy giữa 2 trạm nhờ nhiều cơ chế, đảm bảo chất lượng truyền gửi gói tin, nhưng tốn khá nhiều thời gian để kiểm tra đầy đủ thông tin từ thứ tự dữ liệu cho đến việc kiểm soát vấn đề tắc nghẽn lưu lượng dữ liệu.
- UDP (User Datagram Protocol) gửi dữ liệu từ trạm này tới trạm kia với tốc độ nhanh nhưng không đảm bảo các gói tin đến được tới đích.

### 2.4.Tầng ứng dụng

Là tầng thứ tư trong mô hình TCP/IP. Tầng này cung cấp giao tiếp đến người dùng, cung cấp các ứng dụng cho phép người dùng trao đổi dữ liệu ứng dụng thông qua các dịch vụ mạng khác nhau (như duyệt web, chat, gửi email,...).

Dữ liệu khi đến đây sẽ được định dạng theo kiểu byte nối byte, cùng với đó là các thông tin định tuyến giúp xác định đường đi đúng của một gói tin.

Các giao thức phổ biến:

- FTP (File Transfer Protocol): giao thức chạy trên nền TCP cho phép truyền các file ASCII hoặc nhị phân theo 2 chiều.
- TFTP (Trival File Transfer Protocol) : giao thức truyền file chạy trên nền UDP.
- SMTP ( Simple Mail Transfer Protocol) : giao thức dùng để phân phối thư điện tử.
- Telnet : cho phép truy nhập từ xa để cấu hình thiết bị.
- NMP (Simple Network Managerment Protocol) : Là ứng dụng chạy trên nền UDP , cho phép quản lý và giám sát các thiết bị mạng từ xa.
- DNS (Domain Name System) : Là giao thức phân giải tên miền, được sử dụng trong hỗ trợ truy nhập Internet.
 
 
## 3. So sánh với mô hình OSI

![sosanh](/HoangNH/3.TimhieuTCPIP/image/sosanh.avif)

### 3.1.Điểm giống nhau

- Cả mô hình OSI và TCP/IP đều có cấu trúc các giao thức xếp chồng lên nhau theo các lớp.
- Cả hai đều được coi là mô hình logic.
- Hai mô hình phân chia các giao tiếp mạng thành các lớp rõ ràng.
- Cung cấp các tiêu chuẩn giúp cho nhà sản xuất tạo ra thiết bị. Hệ thống mạng có thể hoạt động, giao tiếp với các thiết bị, hệ thống được sản xuất từ nhà cung cấp khác.

### 3.2.Điểm khác nhau

- TCP/IP chỉ sử dụng tầng ứng dụng để xác định chức năng của các tầng trên. Trong khi đó, OSI sử dụng đến 3 tầng: tầng ứng dụng, tầng trình bày, tầng phiên.
- OSI cần sử dụng 2 tầng vật lý và liên kết dữ liệu để xác định các chức năng của tầng dưới cùng, TCP/IP chỉ sử dụng tầng mạng để thực hiện điều đó.
- Tầng mạng (Network) được mô hình OSI sử dụng để xác định các tiêu chuẩn và giao thức định tuyến. Chức năng này được quản lý bởi tầng mạng (Internet) trong TCP/IP.
- Mô hình TCP/IP là một tiêu chuẩn giao thức định hướng. Còn OSI là một mô hình chung dựa trên chức năng của mỗi lớp.
- Trong TCP/IP, các giao thức được phát triển trước mô hình. Còn đối với mô hình OSI thì ngược lại.
- TCP/IP giúp thiết lập kết nối giữa các thiết bị sử dụng với nhau. OSI giúp chuẩn hóa router, switch, bo mạch chủ và các phần cứng khác.

![bang](/HoangNH/3.TimhieuTCPIP/image/bang.avif)


## 4.Workflow của mô hình TCP/IP

Các bước khi gửi dữ liệu từ A đến B:

- Dữ liệu từ ứng dụng thiết bị qua các giao thức thêm phần Header thành stream chứa thông tin về ứng dụng đích và cổng rồi chuyển đến tầng giao vận.
- Ở tầng giao vận, TCP thêm Header vào các segment, thiết lập kết nối giữa A và B.
- Xử lý dữ liệu thêm thành phần header vào segment rồi chuyển xuống tầng vật lý.
- gói dữ liệu đóng gói thành frame và chuyển thành các bit truyền qua đường truyền vật lý thông qua các thiết bị mạng đến đích.

## 5.Phân biệt giao thức UDP và TCP

![phanbiet](/HoangNH/3.TimhieuTCPIP/image/phanbiet.png)

### 5.1.Giao thức UDP

UDP (User Datagram Protocol) là một giao thức truyền tải dữ liệu không đáng tin cậy trong mạng máy tính. UDP hoạt động dựa trên giao thức IP (Internet Protocol) và thường được sử dụng cho các ứng dụng yêu cầu truyền tải dữ liệu nhanh chóng và hiệu suất cao, như truyền tải âm thanh, video trực tiếp và trò chơi trực tuyến.

UDP tập trung vào tốc độ và hiệu suất, sử dụng cơ chế truyền tải dữ liệu đơn giản hơn, gửi các gói tin gọi là datagram trực tiếp từ nguồn đến đích mà không cần thiết lập kết nối trước.


![udp](/HoangNH/3.TimhieuTCPIP/image/udp.png)

Cách hoạt động cơ bản của UDP:

- Người gửi có thể gửi trực tiếp gói tin đến địa chỉ IP và cổng người nhận
- Dữ liệu được chia thành các gói tin riêng lẻ, mỗi gói tin được đóng gói độc lập.
- Các gói tin có thể bị mất, trùng lặp hoặc đến không đúng thứ tự. UDP không sử dụng cơ chế xác nhận, khôi phục sau lỗi và kiểm soát luồng.
- Sử dụng giao diện IP để định tuyến gói tin trên mạng. Gói tin có địa chỉ nguồn và đích dựa trên địa chỉ IP của các thiết bị
- Không có các quá trình phức tạp như thiết lập kết nối, kiểm soát luồng và xác nhận dữ liệu
- UDP thích hợp cho các ứng dụng yêu cầu tốc độ truyền tải cao

Ứng dụng của UDP: 

- Truyền tải âm thanh, video trực tiếp, game trực tuyến với độ trễ thấp.
- Truyền tải dữ liệu không yêu cầu tính đáng tin cậy như ửi gói tin broadcast hoặc multicast trong mạng nội bộ
- Dùng cho các ứng dụng bắt buộc dữ liệu không bị hao hụt trong quá trình truyền tin.

Ưu điểm của UDP:

- Tốc độ và hiệu suất cao: UDP không có các quá trình thiết lập kết nối và kiểm soát luồng phức tạp như TCP, giúp giảm độ trễ và tăng tốc độ truyền tải dữ liệu.
- Tính nhẹ nhàng và tiết kiêm tài nguyên: thiếu các quá trình phức tạp như thiết lập kết nối, kiểm soát luồng và xác nhận dữ liệu khiến cho UDP phù hợp với môi trường mạng có tải cao hoặc có quy mô lớn.
- UDP có thể truyền phát và truyền đa hướng: một gói tin UDP có thể được gửi đến nhiều người nhận cùng một lúc.

Nhược điểm của UDP:

- Không đảm bảo tính đáng tin cậy: Các gói tin có thể bị mất, trùng lặp hoặc đến không đúng thứ tự.
- Không hỗ trợ kiểm soát luông: có thể dẫn đến tình trạng quá tải mạng hoặc mất mát dữ liệu.
- Không hỗ trợ xác nhận giao nhận: người dùng sẽ không biết gói tin đã được gửi nhận thành công hay không.
- Không hỗ trợ phân đoạn, lắp ghép: khi dữ liệu vượt quá kích thước gói tin thì người dùng phải tự chia nhỏ và ghép nối dữ liệu.

### 5.2.Giao thức TCP

Giao thức TCP (Transmission Control Protocol) là một giao thức lớp vận chuyển đảm bảo việc truyền tải tin nhắn giữa các thiết bị mạng trên Internet.

TCP hoạt động dựa trên mô hình hướng kết nối, nghĩa là trước khi gửi dữ liệu, hai thiết bị mạng cần thiết lập một kết nối tạo thành một đường ống ảo giữa chúng. 

Cách hoạt động cơ bản của TCP:

- Thiết lập kết nối: Một thiết bị gửi một thông điệp (SYN) đến thiết bị đích để bắt đầu thiết lập kết nối. 
Thiết bị nhận phản hồi bằng cách gửi một thông điệp SYN-ACK xác nhận việc nhận thông điệp SYN và sẵn sàng thiết lập kết nối.
Thiết bị gửi sau đó gửi một thông điệp ACK để xác nhận việc nhận thông điệp SYN-ACK từ thiết bị nhận. Kết nối được thiết lập thành công.
- Truyền dữ liệu: Dữ liệu được chia thành các phân đoạn nhỏ hơn và đánh số tuần tự.
- Kiểm soát luồng: Đảm bảo người gửi không gửi quá nhiều dữ liệu khiến người nhận không thể xử lý. 
- Xử lý lỗi và khôi phục: Khi xảy ra lỗi, nó sẽ gửi một ACK có số thứ tự yêu cầu người gửi gửi lại phân đoạn bị mất hoặc bị lỗi. Người gửi nhận được yêu cầu này sẽ gửi lại các phân đoạn bị mất hoặc bị lỗi. 
- Đóng kết nối: Người gửi gửi một thông điệp FIN để cho biết nó đã hoàn thành việc truyền tải dữ liệu.
Người nhận sẽ gửi một ACK để xác nhận việc nhận thông điệp FIN và sẵn sàng đóng kết nối.
Sau đó, người nhận sẽ gửi một thông điệp FIN để yêu cầu đóng kết nối từ phía người gửi.
Cuối cùng, người gửi sẽ gửi một ACK xác nhận việc nhận thông điệp FIN từ người nhận. Kết nối được đóng.

Ứng dụng của TCP:

- Truyền tải dữ liệu trên web (HTTP)
- Gửi nhận Mail (SMTP, POP, IMAP)
- Truyền tải tệp tin (FTP)
- Truyền tải dữ liệu trực tiếp (TCP/IP sockets)
- Tương tác đầu cuối từ xa (Telnet, SSH)
- Truyền tải dữ liệu đa phương tiện (RTSP, RTP)

Ưu điểm của TCP:

- Đảm bảo độ tin cậy: dùng cơ chế xác nhận để đảm bảo dữ liệu được gửi nhận một cách chính xác.
- Dùng cơ chế kiểm soát luồng để điều chỉnh tốc độ truyền tải dữ liệu tránh quá tải
- Hỗ trợ kết nối đa luồng, cho phép nhiều luồng dữ liệu được truyền tải đồng thời trong cùng một kết nối làm tăng hiệu suất truyền tải và sử dụng tài nguyên mạng hiệu quả.
- Hỗ trợ phân đoạn, lắp ghép dữ liệu khắc phục vấn đề kích thước gói tin và tăng hiệu suất truyền tải.

Nhược điểm của TCP:

- Đòi hỏi thời gian thiết lập kết nối.
- Có độ trễ.
- Tốn tài nguyên.
- Không thích hợp cho mạng không đáng tin cậy.


![sosanh](/HoangNH/3.TimhieuTCPIP/image/sosanh.png)