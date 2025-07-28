# Tìm hiểu về mô hình OSI


##  1.Giới thiệu về mô hình OSI
 
Mô hình kết nối các hệ thống mở OSI là mô hình căn bản về các tiến trình truyền thông, thiết lập các tiêu chuẩn kiến trúc mạng ở mức Quốc tế, là cơ sở chung để các hệ thống khác nhau có thể liên kết và truyền thông được với nhau. 

Mô hình OSI tổ chức các giao thức truyền thông thành 7 tầng, mỗi một tầng giải quyết một phần hẹp của tiến trình truyền thông, chia tiến trình truyền thông thành nhiều tầng và trong mỗi tầng có thể có nhiều giao thức khác nhau thực hiện các nhu cầu truyền thông cụ thể.


## 2.Các tầng trong mô hình OSI

### 2.1.Tầng vật lý (Physical layer)

Tầng vật lý là tầng thấp nhất trong mô hình OSI.Tầng vật lý là phương tiện truyền dẫn vật lý và các công nghệ để truyền dữ liệu qua phương tiện đó.

Đây cũng là tầng nơi dữ liệu được chuyển đổi thành một luồng bit, là một chuỗi gồm các số 1 và 0. Tầng vật lý của cả hai thiết bị cũng phải đồng ý về một quy ước tín hiệu để các số 1 có thể được phân biệt với các số 0 trên cả hai thiết bị.

![image1](/HoangNH/2.TimhieuOSI/image/image1.png)

### 2.2.Tầng liên kết dữ liệu (Data link layer)

Tầng liên kết dữ liệu là tầng thứ hai trong mô hình OSI.

Chức năng chủ yếu của tầng liên kết dữ liệu là thực hiện thiết lập các liên kết, duy trì và hủy bỏ các liên kết dữ liệu, kiểm soát lỗi và kiểm soát lưu lượng.

Tầng này quản lý khung dữ liệu(frame) – là các tín hiệu kỹ thuật số được gói gọn trong các gói dữ liệu.Trong các mạng quảng bá, tầng con MAC (Medium Access Sublayer) điều khiển việc duy trì nhập đường truyền.

header kt mac nguồn , mac ích có giống k, giống thì cho lên. k xóa thì k ọc úng, thì tầng k ọc ược.

![image2](/HoangNH/2.TimhieuOSI/image/image2.png)
### 2.3.Tầng mạng (Network Layer)

Tầng mạng là tầng thứ ba trong mô hình OSI.

Tầng mạng liên quan đến các khái niệm như định tuyến, chuyển tiếp và xác định địa chỉ trên một mạng phân tán hoặc nhiều mạng được kết nối của các nút hoặc máy. 

Tầng mạng thực hiện các chức năng chọn đường đi (routing) cho các gói tin nguồn tới đích có thể trong cùng một mạng hoặc khác mạng nhau. 

Tầng mạng còn có chức năng điều khiển tắc nghẽn (Congestion Control). Nếu có quá nhiều gói tin cùng lưu chuyển trên cùng một đường thì có thể xảy ra tình trạng tắc nghẽn. Thực hiện chức năng giao tiếp giữa các mạng khi các gói tin đi từ mạng này sang mạng khác để tới đích.

ip nguồn va ip ích, k úng thì tìm ip khác bằng bảng ịnh tuyến, úng thì nhận. 

![image3](/HoangNH/2.TimhieuOSI/image/image3.png)
h
### 2.4.Lớp vận chuyển (Transport layer)

Đây là tầng thứ tư trong mô hình OSI và là tầng cao nhất liên có liên quan đến các giao thức trao đổi dữ liệu giữa các hệ thống mở, kiểm soát việc truyền dữ liệu từ nút tới nút (End-to-End).

Tầng vận chuyển thực hiện việc chia các gói tin lớn thành các gói tin nhỏ hơn trước khi gửi đi và đánh số các gói tin và đảm bảo chúng chuyển theo đúng thứ tự.

Các giao thức được sử dụng:

- Giao thức điều khiển truyền tải (Transmission Control Protocol – TCP) dựa trên kết nối gần như không suy hao
  + sử dụng khi tất cả dữ liệu phải còn nguyên vẹn. Ví dụ: chia sẻ tệp
- Giao thức gói dữ liệu người dùng (User Datagram Protocol – UDP) không kết nối có suy hao.
  + sử dụng khi việc giữ lại tất cả các gói ít quan trọng hơn. Ví dụ: truyền phát video

![image4](/HoangNH/2.TimhieuOSI/image/image4.png)

### 2.5.Tầng phiên (Session layer)

Tầng phiên là tầng thứ năm trong mô hình OSI. Tầng này đáp ứng các yêu cầu dịch vụ của tầng trình diễn và gửi các yêu cầu dịch vụ tới tầng vận chuyển.
Tầng phiên cho phép người sử dụng trên các máy khác nhau thiết lập, duy trì và đồng bộ phiên truyền thông giữa họ với nhau.

Các chức năng: 

- Kiểm soát hội thoại: Tầng phiên cho phép 2 thực thể (tiến trình) cùng tham gia vào một cuộc hội thoại. Nó cho phép truyền thông giữa 2 tiến trình được thực hiện hoặc theo chế độ half duplex hoặc full duplex.
- Đồng bộ hoá: Tầng phiên cho phép một tiến trình thêm các mốc vào luồng dữ liệu

![image5](/HoangNH/2.TimhieuOSI/image/image5.png)

### 2.6.Tầng trình bày (Presentation layer)

Tầng trình bày là tầng thứ sáu trong mô hình OSI.Tầng trình bày giải quyết các vấn đề liên quan đến các cú pháp và ngữ nghĩa của thông tin được truyền.

Tầng trình bày được sử dụng để thể hiện các chức năng đồng bộ hóa các hiển thị giữa 2 người dùng.

Có 3 chức năng cơ bản:

- dịch: nhận dữ liệu từ lớp ứng dụng, chuyển từ các ký tự và số sang mã nhị phân
- nén: nén các dữ liệu nhận được từ tầng ứng dụng trước khi phân phối đến tầng phiên, giúp cải thiện tốc độ và hiệu quả của giao tiếp bằng cách giảm thiểu lượng dữ liệu sẽ được truyền.
- mã hóa/giải mã: trước khi dữ liệu được truyền thì sẽ được mã hóa. Ở phía người gửi, dữ liệu được mã hóa và ở phía người nhận dữ liệu được giải mã. Sử dụng giao thức SSL để mã hóa và giải mã.

![image6](/HoangNH/2.TimhieuOSI/image/image6.png)

### 2.7.Tầng ứng dụng (Application layer)
Tầng ứng dụng là tầng cao nhất trong mô hình OSI.Tầng này có chức năng giao tiếp trực tiếp với các tiến trình của ứng dụng và thi hành những dịch vụ thông thường của các tiến trình đó.

Tầng ứng dụng xác định giao diện người dùng sử dụng và môi trường OSI. Tầng này gồm nhiều các giao thức ứng dụng cung cấp các phương diện cho người sử dụng truy cập vào môi trường mạng và cung cấp các dịch vụ phân tán.

Các giao thức và dịch vụ phổ biến như:
- HTTP - Hypertext Transfer Protocol
- FTP (File Transfer Protocol)
- SMTP (Simple Mail Transfer Protocol)
- DNS (Domain Name System)
- SNMP (Simple Network Management Protocol)

![image7](/HoangNH/2.TimhieuOSI/image/image7.png)


## 3. Workflow với mô hình OSI

![image8](/HoangNH/2.TimhieuOSI/image/image8.avif)

Các bước đóng gói dữ liệu trong mô hình OSI:
- Bước 1: Đưa thông tin cần gửi vào máy tính
  - Ở tầng ứng dụng, người dùng tiến hành đưa thông tin cần gửi vào máy tính. Các thông tin này thường có dạng như: hình ảnh, văn bản, số, ứng dụng trên điện di động,...
  - Sau đó các dữ liệu này được đưa xuống tầng trình bày để chuyển hóa các dữ liệu thành một dạng chung để mã hóa dữ liệu và nén dữ liệu.
  - Tiếp đến gửi đến tầng phiên để bổ sung các thông tin cần thiết cho một phiên giao dịch (gửi-nhận) đồng thời.
- Bước 2: Các gói tin sẽ được vận chuyển xuống tầng giao vận
  - Các gói tin này là 1 Data được đóng thêm một TCP header hoặc UDP header phần này sẽ được gọi là 1 segments, segments chứa 2 thành phần chính TCP/UDP header và data. Segments sẽ được đưa xuống tầng tiếp theo là tầng mạng.
- Bước 3: Đóng thêm IP header vào Segments
  - Tầng mạng thực hiện đóng thêm 1 IP header vào Segments được gọi là Packet. Packet chứa IP header , TCP/UDP header và Data.
- Bước 4: Gói tin chuyển xuống tầng liên kết dữ liệu và tầng vật lý
  - thực hiện việc dán địa chỉ mac cổng thiết bị hiện tại và mac đích (mac của cổng router phía trước). Ở tầng liên kết dữ liệu ,việc bọc thêm ethernet header lúc này sẽ được gọi là Frames. Dữ liệu này sẽ được chuyển hóa thành một dòng Bit nhị phân để truyền trên đường truyền vật lý.
- Bước 5: Ở phía đầu thu, quá trình lại diễn ra ngược lại tức là lúc này dòng Bit nhị phân được đưa vào đường truyền vật lý và truyền lên trên.
- Bước 6: Gói tin tiếp tụ được đẩy lên tầng trên Datalink
  - Ở tầng vật lý thì dữ liệu sẽ được tiếp tục đẩy lên tầng trên liên kết dữ liệu. Bóc 1 lớp gói hàng ra được gọi ethernet header ra ở tầng liên kết dữ liệu gọi là lớp Frames và tương tự đẩy lên tầng mạng và bóc lớp Packets tương tự như vậy đến tầng vận chuyển bóc Segments và đẩy lên tầng trên của nó.

Quá trình đóng gói diễn ra ở phía người gửi diễn ra như sau: dữ liệu của người dùng được gọi là user data sẽ đi từ trên Application xuống từng lớp từng lớp một và không được bỏ qua bất kỳ lớp nào, khi đi tới 1 lớp user data sẽ được bọc vào trong header của lớp đó. Ở lớp 7 sẽ có layer 7 header, xuống lớp 6 sẽ có layer 6 header, riêng lớp 2 ngoài layer 2 header còn có phần trailer kiểm tra lỗi FCS (Frame Check Sequence), khi đi xuống lớp 1 sẽ chuyển thành bit nhị phân và truyền đi. Phần header chính là phần thông tin quản lý của gói tin còn data chính là phần dữ liệu thực sự của gói tin.

Quá trình mở gói diễn ra ở phía người nhận sẽ ngược lại, dữ liệu sẽ đi ngược từ dưới lên trên, khi đi tới 1 lớp nào sẽ được gỡ bỏ header của lớp đó và cuối cùng trả về user data cho người dùng. Đầu tiên toàn bộ dãy bit nhị phân sẽ được chuyển thành 1 khung dữ liệu, đi lên lớp 2 sẽ được kiểm tra FCS và gỡ bỏ layer 2 header, lên lớp 3 sẽ được gỡ layer 3 header, tương tự đến layer 7 sau khi gỡ bỏ layer 7 header sẽ trả về user data cho người dùng.

Các lớp dưới cung cấp dịch vụ trực tiếp cho các lớp ngay phía trên nó. Các lớp trên sẽ gửi yêu cầu xuống lớp dưới và nhận lại kết quả, các lớp trên không cần biết hoạt động cụ thể diễn ra tại lớp dưới, hoạt động của lớp dưới hoàn toàn trong suốt với lớp trên.

