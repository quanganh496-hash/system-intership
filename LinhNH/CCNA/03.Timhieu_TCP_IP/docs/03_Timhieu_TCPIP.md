# **Tìm hiểu về mô hình TCP/IP** 
# Mục lục
1. [Khái quát về mô hình TCP/IP](#1-khái-quát-về-mô-hìnhtcpip)
2. [Cấu trúc mô hình TCP/IP](#2-cấu-trúc-mô-hình-tcpip)  
    2.1 [Tầng vật lý](#21-tầng-vật-lý)  
    2.2 [Tầng mạng](#22-tầng-mạng)  
    2.3 [Tầng giao vận](#23-tầng-giao-vận)  
    2.4 [Tầng ứng dụng](#24-tầng-ứng-dụng)  
    2.5 [Các giao thức TCP/IP phổ biến nhất](#25-các-giao-thức-tcpip-phổ-biến-nhất)  
3. [So sánh giữa mô hình OSI và TCP/IP](#3-so-sánh-giữa-mô-hình-osi-và-tcpip)
4. [Workflow với mô hình TCP/IP](#4-workflow-với-mô-hình-tcpip)
5. [Phân biệt giao thức UDP và TCP](#5-phân-biệt-giao-thức-udp-và-tcp)  
    5.1 [Tổng quan về giao thức UDP](#51-tổng-quan-về-giao-thức-udp)  
    5.2 [So sánh giữa UDP - TCP](#52-so-sánh-giữa-udp---tcp)  
--------
## 1. Khái quát về mô hìnhTCP/IP
- **`TCP/IP`**  (Transmission Control Protocol/ Internet Protocol) là giao thức điều khiển để truyền nhận liên mạng. Đây là một bộ giao thức có chức năng truyền và kết nối các thông tin giữa các thiết bị trong một mạng lưới internet.

![hinh_1](/LinhNH/CCNA/03.Timhieu_TCP_IP/images/TcpIP.png)
- **`Chức năng hoạt động`**
    - ***TCP*** : Giao thức kiểm soát truyền tải.
    
    Có chức năng xác định các ứng dụng và tạo ra các kênh giao tiếp. TCP cũng có chức năng quản lý các thông tin khi được chia nhỏ để truyền tải qua internet. Giao thức này sẽ tập hợp các thông tin này theo đúng thứ tự, đảm bảo truyền tải thông tin chính xác tới địa chỉ đến. 
    - ***IP*** : Giao thức Internet  

    Đảm bảo thông tin được truyền đến đúng địa chỉ. IP sẽ gán các địa chỉ và định tuyến từng gọi thông tin. Mỗi mạng sẽ có 1 địa chỉ IP để xác định được chính xác nơi chuyển/nhận thông tin, dữ liệu.  

**Cấu trúc gói tin:** 1 gói tin TCP bao gồm 2 phần:  
- Header (có độ dài 20 bytes)  
- Dữ liệu    

> Phần header: có 11 trường trong đó 10 trường bắt buộc. Trường thứ 11 là tùy chọn (trong bảng minh họa có màu nền đỏ)

![hinh_1](/LinhNH/CCNA/03.Timhieu_TCP_IP/images/Cau-truc-goi-tin-TCP.png)

- Source port (16 bit): số cổng của tiến trình gửi
- Destination port (16 bit): số cổng của tiến trình nhận
- Sequence number (32 bit): số thứ tự (phụ thuộc vào giá trị của bit SYN)
- Acknowledgement number (32 bit): số báo nhận. Trường số thứ tự và số báo nhận dùng để đảm bảo dịch vụ truyền dữ liệu tin cậy
- Các trường flag (6 trường, mỗi trường 1 bit):

  - ACK: xác nhận danh tính chính xác của giá trị trường Acknowledgement
  - RST, SYN, FIN: thiết lập và hủy bỏ kết nối
  - PSH: chỉ định máy nhận phải chuyển dữ liệu lên tầng trên ngay lập tức
  - URG: chỉ định vùng dữ liệu được đánh dấu "urgent" (dữ liệu chuẩn)
- Checksum (16 bit): sử dụng để kiểm tra lỗi
- Window size (16 bit): kích thước cửa sổ dùng trong kiểm soát luồng
- Reserved (3 bit): luôn chứa giá trị 000, để dành sử dụng trong tương lai
- Data offset (4 bit): kích thước của TCP header.
- Urgent pointer: nếu cờ URG bật thì giá trị trường này chính là số từ 16 bít mà số thứ tự gói tin (sequence number) cần dịch trái.
- Options (độ dài thay đổi): được sử dụng khi hai máy tham gia truyền thông thỏa thuận về kích thước tối đa của segment

## 2. Cấu trúc mô hình TCP/IP
- Mô hình TCP/IP tiêu chuẩn bao gồm 4 tầng được chồng lên nhau là:  
Tầng 1: Tầng vật lý (Network Access)  
Tầng 2: Tầng mạng (Internet)  
Tầng 3: Tầng giao vận (Transport)  
Tầng 4: Tầng ứng dụng (Application)      

![hinh_2](/LinhNH/CCNA/03.Timhieu_TCP_IP/images/Layer.png)
### 2.1 Tầng vật lý
- Đây là tầng thấp nhất trong mô hình TCP/IP, đóng vai trò truyền dữ liệu giữa 2 thiết bị trong cùng 1 mạng. Ở tầng này, toàn bộ gói dữ liệu sẽ được đóng vào khung (Frame) và được định tuyến đi đến đích đã được chỉ định ban đầu.  
-  Lớp này là một nhóm phương thức vận hành trên một kết nối của máy chủ, thường được biết đến là Ethernet.
### 2.2 Tầng mạng
Đây là lớp kết nối các mạng nội bộ với nhau, còn được gọi là tầng Mạng. **Lớp Internet**  sẽ xử lý quá trình truyền gói tin trên mạng. Các giao thức của lớp này bao gồm:  
- IP – Internet Protocol  
- ICMP-Internet Control Message Protocol  
- IGMP- Internet Group Message Protocol
### 2.3 Tầng giao vận
Đây là lớp điều khiển giao tiếp máy chủ tới máy chủ, còn được gọi là Tầng giao vận.
Lớp truyền tải sẽ phụ trách luồng dữ liệu giữa 2 trạm thực hiện các ứng dụng của lớp trên. Lớp này có 2 giao thức chính là:  
- **TCP** – Transmission Control Protocol: cung cấp luồng dữ liệu tin cậy giữa 2 trạm nhờ nhiều cơ chế. Ví dụ như chia nhỏ các gói tin ở tầng trên thành các gói tin có kích thước thích hợp cho tầng mạng bên dưới, báo nhận gói tin, đặt hạn chế thời gian timeout để đảm bảo bên nhận biết được các gói tin đã gửi đi.  
- **UDP** – User Datagram Protocol: gửi dữ liệu từ trạm này tới trạm kia mà không đảm bảo các gói tin đến được tới đích.
### 2.4 Tầng ứng dụng   

Đây là một tập hợp các giao thức cụ thể giao tiếp dữ liệu trên một lớp quá trình tới quá trình.   
`Chức năng` :
- Nó cung cấp giao tiếp đến người dùng.
- Cung cấp các ứng dụng cho phép người dùng trao đổi dữ liệu ứng dụng thông qua các dịch vụ mạng khác nhau (như duyệt web, chat, gửi email,...).
- Dữ liệu khi đến đây sẽ được định dạng theo kiểu Byte nối Byte, cùng với đó là các thông tin định tuyến giúp xác định đường đi đúng của một gói tin.   

`Một số giao thức trao đổi dữ liệu` :

- **FTP** (File Transfer Protocol): giao thức chạy trên nền TCP cho phép truyền các file ASCII hoặc nhị phân theo 2 chiều.
- **TFTP** (Trival File Transfer Protocol) : giao thức truyền file chạy trên nền UDP.
- **SMTP** ( Simple Mail Transfer Protocol) : giao thức dùng để phân phối thư điện tử.
- **Telnet** : cho phép truy nhập từ xa để cấu hình thiết bị.
- **SNMP** (Simple Network Managerment Protocol) : Là ứng dụng chạy trên nền UDP , cho phép quản lý và giám sát các thiết bị mạng từ xa.
- **Domain Name System** ( DNS) : Là giao thức phân giải tên miền, được sử dụng trong hỗ trợ truy nhập Internet.

### 2.5 Các giao thức TCP/IP phổ biến nhất
#### a. HTTP
- HTTP là giao thức của TCP/IP được sử dụng phổ biến để phân phối dữ liệu không an toàn (gồm các file ảnh, tệp HTML,…) giữa web client với một web server. Trình duyệt web trên máy tính sẽ gửi yêu cầu đến web server để biết thông tin về một website. Khi web server nhận được yêu cầu nó sẽ xác nhận và gửi thông tin về website cho trình duyệt internet trên máy tính – web client. HTTP có 3 đặc trưng cơ bản là kết nối không liên tục, hoạt động độc lập và stateless.
#### b. HTTPS
- HTTPS là một giao thức của TCP/IP, nó có sự kết hợp giữa SSL và TLS. HTTPS được sử dụng phổ biến khi muốn gửi dữ liệu cần bảo mật cao như thẻ tín dụng, dữ liệu cá nhân từ một website đến một web server.

![hinh_2.5](/LinhNH/CCNA/03.Timhieu_TCP_IP/images/Giao-thuc-http-https.png)


#### c. FTP
- FTP là một giao thức của TCP/IP, được sử dụng để trao đổi dữ liệu giữa hai hoặc nhiều máy tính qua internet. FTP hoạt động trên hai cổng là 20 và 21. Nhờ FTP, các máy client trong mạng có khả năng truy cập đến máy chủ để gửi và lấy dữ liệu. Điểm đặc biệt của giao thức này là giúp người dùng dù đang ở xa vẫn có thể truy cập vào máy chủ để truyền hoặc nhận dữ liệu.

![hinh_2.5](/LinhNH/CCNA/03.Timhieu_TCP_IP/images/Giao-thuc-ftp.png)

## 3. So sánh giữa mô hình OSI và TCP/IP
![hinh_3](/LinhNH/CCNA/03.Timhieu_TCP_IP/images/So-sanh-osi-tcp-ip.png)

`Giống nhau` :  
- Cả 2 đều sử dụng mô hình kiến trúc phân lớp  
- Đều có tầng Application mặc dù dịch vụ khác nhau  
- Đều có tầng Transport, Network (ở mô hình TCP/IP là Internet)  
- Sử dụng kĩ thuật chuyển tin đóng gói Packet  

` Khác nhau` :

|Mô hình OSI| Mô hình TCP/IP|
|:---------|:-------------|
|Do ISO nghiên cứu và phát triển|Do ARPANET nghiên cứu và phát triển|
|Có sự phân biệt rõ ràng giữa các giao diện, dịch vụ và giao thức|Dịch vụ, giao diện và giao thức không có sự phân biệt|
|Liên quan với Kết nối hệ thống mở|Liên quan với Giao thức điều khiển truyền dẫn|
|OSI sử dụng nhiều lớp mạng|TCP/IP tiếp cận theo chiều ngang|
|Có tổng cộng 7 lớp|Có tổng cộng 4 lớp|
|Lớp truyền tải xác định hướng kết nối|Chỉ ra hướng kết nối và hướng không kết nối|
|Lớp liên kết phần cứng tách biệt với lớp liên kết phần mềm|Trong TCP, cả liên kết vật lý và dữ liệu đều được kết hợp dưới dạng một lớp máy chủ đến mạng|
|Các lớp phiên và trình bày là một phần của mô hình OSI|Không có lớp phiên và lớp trình bày|
|Xuất hiện sau khi có Internet|Xuất hiện trước khi có Internet|
|Header tối thiểu là 5 byte|Header tối thiểu là 20 byte|
-----------------

## 4. Workflow với mô hình TCP/IP
_Khi A gửi một dữ liệu (thông tin) đến B thì sẽ trải qua quá trình bắt tay 3 bước :_
- **Bước 1:** Máy chủ A khởi tạo kết nối bằng cách gửi gói TCP SYN đến máy chủ đích B. Gói chứa số thứ tự ngẫu nhiên (ví dụ: 5432) đánh dấu sự bắt đầu của số thứ tự cho dữ liệu mà Máy chủ A sẽ truyền.  
- **Bước 2:** Máy chủ B nhận gói và phản hồi bằng số thứ tự của chính nó. Phản hồi cũng bao gồm số xác nhận, là số thứ tự của Máy chủ A được tăng thêm 1 (ví dụ như: 5433).  
- **Bước 3:** Máy chủ A xác nhận phản hồi của Máy chủ B bằng cách gửi số xác nhận, là số thứ tự của Máy chủ B tăng thêm 1.  

![hinh_4](/LinhNH/CCNA/03.Timhieu_TCP_IP/images/Workflow-tcp-ip.png)

**`Thiết lập kết nối (Connection Establishment):`**  
Một thiết bị (được gọi là người gửi) gửi một thông điệp SYN (synchronize) đến thiết bị đích (được gọi là người nhận) để bắt đầu quá trình thiết lập kết nối.
- Thiết bị nhận phản hồi bằng cách gửi một thông điệp SYN-ACK (synchronize-acknowledge) xác nhận việc nhận thông điệp SYN và sẵn sàng thiết lập kết nối.
- Thiết bị gửi sau đó gửi một thông điệp ACK (acknowledge) để xác nhận việc nhận thông điệp SYN-ACK từ thiết bị nhận. Kết nối được thiết lập thành công.  

**`Truyền dữ liệu (Data Transmission):`**    
Sau khi kết nối được thiết lập, các thiết bị có thể bắt đầu truyền tải dữ liệu. Dữ liệu được chia thành các phân đoạn nhỏ hơn và đánh số tuần tự.
Người gửi gửi các phân đoạn này đến người nhận qua kết nối đã thiết lập. Mỗi phân đoạn được đánh số thứ tự để cho phép người nhận xác định và lắp ráp chúng lại theo đúng thứ tự ban đầu.

**`Kiểm soát luồng (Flow Control):`**  
TCP sử dụng cơ chế kiểm soát luồng để đảm bảo rằng người gửi không gửi quá nhiều dữ liệu mà người nhận không thể xử lý.
- Người nhận sử dụng cơ chế xác nhận (ACK) để thông báo cho người gửi biết rằng dữ liệu đã được nhận thành công.
- Người gửi điều chỉnh tốc độ truyền tải dựa trên thông tin ACK và các thông số kiểm soát luồng như cửa sổ trượt (sliding window).  

**`Xử lý lỗi và khôi phục (Error Handling and Recovery):`**  
Nếu người nhận không nhận được một phân đoạn hoặc xảy ra lỗi trong quá trình truyền tải, nó sẽ gửi một ACK có số thứ tự yêu cầu người gửi gửi lại phân đoạn bị mất hoặc bị lỗi. Người gửi nhận được yêu cầu này sẽ gửi lại các phân đoạn bị mất hoặc bị lỗi. Quá trình này được gọi là khôi phục (recovery) và sử dụng cơ chế retransmission. 

**`Đóng kết nối (Connection Termination):`**  
Khi quá trình truyền tải hoàn tất, hai thiết bị có thể đóng kết nối.
Người gửi gửi một thông điệp FIN (finish) để cho biết nó đã hoàn thành việc truyền tải dữ liệu.
Người nhận sẽ gửi một ACK để xác nhận việc nhận thông điệp FIN và sẵn sàng đóng kết nối.
Sau đó, người nhận sẽ gửi một thông điệp FIN để yêu cầu đóng kết nối từ phía người gửi.
Cuối cùng, người gửi sẽ gửi một ACK xác nhận việc nhận thông điệp FIN từ người nhận. Kết nối được đóng.

![hinh_4](/LinhNH/CCNA/03.Timhieu_TCP_IP/images/Workflow-TCPIP.png)

## 5. Phân biệt giao thức UDP và TCP
### 5.1 Tổng quan về giao thức UDP
#### a. Giao thức UDP
**UDP** (User Datagram Protocol) – Giao thức dữ liệu người dùng là một giao thức giao tiếp thay thế cho TCP – 
giao thức kiểm soát đường truyền, được sử dụng chủ yếu để thiết lập các kết nối có độ trễ thấp và không chịu lỗi giữa các ứng dụng trên internet.  
#### b. Cấu trúc gói tin UDP  
![hinh_5.1](/LinhNH/CCNA/03.Timhieu_TCP_IP/images/Cautruc-UDP.png)
- **Port nguồn** (Source Port) (2 byte)  
Đây là số cổng của máy gửi dữ liệu. Số cổng này xác định ứng dụng nguồn mà dữ liệu đang được gửi.  
- **Port đích** (Destination Port) (2 byte)  
Đây là số cổng của máy nhận dữ liệu, xác định ứng dụng đích mà dữ liệu sẽ được chuyển đến.    
- **Độ dài gói tin** (Length) (2 byte)  
Đây là yếu tố xác định độ dài tổng của gói tin UDP, bao gồm cả tiêu đề và dữ liệu. Độ dài gói tin tính bằng byte.
- **Kiểm tra CRC** (Checksum) (2 byte)  
Yếu tố này sử dụng giá trị CRC (Cyclic Redundancy Check) để kiểm tra tính toàn vẹn của gói tin. Kiểm tra CRC giúp phát hiện các lỗi trong quá trình truyền dữ liệu, nhưng không thực hiện việc sửa chữa lỗi.  
- **Dữ liệu** (Data) (N byte)  
Đây là nội dung của gói tin, có độ dài thay đổi tuỳ vào ứng dụng đã sử dụng UDP.
#### c. Cách thức hoạt động
Giao thức UDP hoạt động như sau:  
- **Gửi dữ liệu:** Khi một ứng dụng muốn gửi dữ liệu cho một ứng dụng khác, nó sẽ gọi hàm của giao thức UDP để gửi dữ liệu.  
- **Tạo datagram:** Giao thức UDP sẽ lấy dữ liệu từ ứng dụng và chèn thêm một số trường điều khiển vào dữ liệu, bao gồm hai trường địa chỉ cổng nguồn và đích.    
- **Gửi datagram tới tầng mạng:** Giao thức UDP sẽ gửi datagram tới tầng mạng.    
- **Gửi datagram tới máy tính nhận:** Tầng mạng sẽ gửi datagram tới máy tính nhận.      
- **Nhận dữ liệu:** Khi máy tính nhận nhận được datagram, nó sẽ gọi hàm của giao thức UDP để nhận dữ liệu.  
![hinh_5.1](/LinhNH/CCNA/03.Timhieu_TCP_IP/images/UDP.png)
### 5.2 So sánh giữa UDP - TCP
![hinh_5.2](/LinhNH/CCNA/03.Timhieu_TCP_IP/images/So-sanh-tcp-udp.png)  
**_Bảng so sánh_**
|Tính năng|TCP|UDP|  
|:--------------|:-----------|:------|
|Cơ chế kết nối|Thiết lập kết nối trước khi truyền dữ liệu. TCP sử dụng cơ chế bắt tay (handshake) để thiết lập một kết nối đáng tin cậy giữa máy gửi và máy nhận trước khi truyền dữ liệu| Không thiết lập kết nối trước khi truyền dữ liệu. UDP truyền gói tin mà không cần thiết lập một liên kết đầy đủ|
|Quản lý trạng thái kết nối|Duy trì trạng thái kết nối liên tục giữa máy gửi và máy nhận trong suốt quá trình truyền dữ liệu. Mọi gói tin được gửi và nhận trong ngữ cảnh của kết nối đã thiết lập| Không duy trì trạng thái kết nối liên tục giữa máy gửi và máy nhận. Mỗi gói tin UDP độc lập với các gói tin khác| 
|Giải trình tự dữ liệu|Có trình tự|Không trình tự|
|Đảm bảo tính toàn vẹn và xác minh|Đảm bảo|Không đảm bảo|
|Truyền lại dữ liệu gói bị mất|Truyền lại được|Không truyền lại được|
|Kiểm tra lỗi|Kiểm tra lỗi mở rộng và xác nhận dữ liệu|Tổng kiểm tra cơ bản|
|Phương thức truyền nhận|Dữ liệu đọc dưới dạng luồng byte, thông diệp được truyền đến ranh giới phân đoạn|Ranh giới xác định, gửi riêng lẻ và kiểm tra tính toàn vện khi đến nơi|
|Tốc độ|Chậm hơn UDP|Nhanh hơn TCP|
|Phát sóng|Không hỗ trợ phát sóng|Có hỗ trợ phát sóng|
|Sử dụng tối ưu|Được sử dụng bởi HTTPS, HTTP, SMTP, POP, FTP, v.v.|Hội nghị truyền hình, phát trực tuyến, DNS, VolP, v.v.|  
---------
