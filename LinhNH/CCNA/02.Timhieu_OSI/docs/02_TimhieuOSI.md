# **Tìm hiểu về mô hình OSI** 

# Mục lục
1. [Khái quát về mô hình OSI](#1-khái-quát-về-mô-hình-osi )
2. [Các tầng trong mô hình OSI](#2-các-tầng-trong-mô-hình-osi)  
    2.1 [Tầng vật lý](#21-tầng-vật-lý-physical-layer)  
    2.2 [Tầng liên kết dữ liệu](#22-tầng-liên-kết-dữ-liệu-data-link-layer)  
    2.3 [Tầng mạng](#23-tầng-mạng-network-layer)  
    2.4 [Tầng giao vận](#24-tầng-giao-vận-transport-layer)  
    2.5 [Tầng phiên](#25-tầng-phiên-session-layer)  
    2.6 [Tầng trình diễn](#26-tầng-trình-diễn-presentation-layer)  
    2.7 [Tầng ứng dụng](#27-tầng-ứng-dụng-application-layer)  
3. [Workflow với mô hình OSI](#3-workflow-với-mô-hình-osi)
-------------
## 1. Khái quát về mô hình OSI
**Mô hình OSI** (_Open Systems Interconnection_) là một mô hình tham chiếu để mô tả cách mà các hệ thống mạng giao tiếp với nhau. Mô hình OSI phân chia quá trình giao tiếp mạng thành các tầng độc lập nhằm tăng tính tương thích và tách biệt giữa các phần của một hệ thống mạng.  

![hinh_0](/LinhNH/CCNA/02.Timhieu_OSI/images/Mo_hinh_OSI.png)  
Mô hình OSI phân chia quá trình truyền thông mạng thành 7 tầng khác nhau. Mỗi tầng có chức năng và nhiệm vụ riêng, đồng thời tương tác với nhau để đảm bảo việc truyền thông dữ liệu hiệu quả.   

![hinh_1](/LinhNH/CCNA/02.Timhieu_OSI/images/Layer.png)

## 2. Các tầng trong mô hình OSI

### 2.1 Tầng vật lý (Physical layer)

- __Tầng Vật lý__ (Physical Layer) là tầng thấp nhất trong các tầng OSI, đảm bảo việc truyền dữ liệu qua môi trường vật lý và không quan tâm đến nội dung hay ý nghĩa của dữ liệu. Nó tạo ra một đường truyền vật lý ổn định và đáng tin cậy để các tầng cao hơn có thể gửi và nhận các gói tin dữ liệu.  

![hinh_2.1](/LinhNH/CCNA/02.Timhieu_OSI/images/Physical_Layer.png)

- Nhiệm vụ của tầng Vật lý bao gồm:
  - __Truyền dữ liệu__: Tầng Vật lý biến các bit thành tín hiệu vật lý để truyền qua các phương tiện truyền thông như cáp đồng trục, cáp xoắn đôi, cáp quang hay sóng vô tuyến. Nó xác định các quy tắc về tốc độ truyền, đồng bộ hóa, kích thước khung dữ liệu, phạm vi tín hiệu và các thông số vật lý khác.
  - __Điều khiển tín hiệu__: Tầng Vật lý quản lý các tín hiệu điều khiển như tín hiệu báo động, tín hiệu đồng bộ, tín hiệu kiểm tra lỗi, và tín hiệu điều chỉnh tốc độ truyền dữ liệu.
  - __Định dạng dữ liệu__: Tầng Vật lý xác định cấu trúc và định dạng của dữ liệu trong từng bit, ví dụ như định dạng NRZ (Non-Return-to-Zero), Manchester, AMI (Alternate Mark Inversion) và các phương pháp khác.
  - __Mã hóa và giải mã__: Tầng Vật lý thực hiện mã hóa và giải mã các tín hiệu để đảm bảo việc truyền dữ liệu chính xác.

### 2.2 Tầng liên kết dữ liệu (Data Link layer)
- Tầng Liên kết dữ liệu là tầng thứ hai trong mô hình OSI. Nó chịu trách nhiệm cho việc truyền dữ liệu an toàn qua các đường truyền vật lý và xác định địa chỉ vật lý (MAC address). Tầng Liên kết dữ liệu cung cấp các dịch vụ cho tầng mạng và có hai phân lớp con:

  - __Lớp LLC__ (Logical Link Control): Lớp LLC quản lý các quy tắc truyền thông đồng bộ và không đồng bộ, kiểm soát lỗi và kiểm tra tính toàn vẹn của dữ liệu. Nó đảm bảo việc truyền thông tin một cách tin cậy giữa các điểm cuối trên cùng một mạng liên kết.
  - __Lớp MAC__ (Media Access Control): Lớp MAC xác định cách truy cập vào phương tiện truyền thông chia sẻ, chẳng hạn như mạng LAN Ethernet. Nó quản lý việc gán địa chỉ vật lý (MAC address) cho các thiết bị mạng và xử lý việc truyền dữ liệu giữa các đầu cuối trên cùng một mạng.

![hinh_2.2](/LinhNH/CCNA/02.Timhieu_OSI/images/DataLink_Layer.png)


- Tầng Liên kết dữ liệu có các chức năng quan trọng sau:

  - __Đóng gói dữ liệu__: Tầng này chia dữ liệu từ tầng mạng thành các khung dữ liệu nhỏ hơn để truyền qua đường truyền vật lý.
  - __Định địa chỉ vật lý__: Tầng Liên kết dữ liệu sử dụng địa chỉ MAC để xác định nguồn và đích của các khung dữ liệu.
  - __Kiểm soát lỗi__: Tầng này thực hiện kiểm tra lỗi, phát hiện và xử lý các vấn đề liên quan đến sự mất mát hoặc hỏng hóc dữ liệu ở tầng Vật lý.
  - __Kiểm soát truy cập vào phương tiện truyền thông__: Tầng Liên kết dữ liệu quản lý quy tắc truy cập vào môi trường chia sẻ, đảm bảo rằng các thiết bị không xung đột và có thể truyền dữ liệu một cách hiệu quả.
### 2.3 Tầng mạng (Network layer)
- Network layer là gì? Tầng Mạng (Network Layer) là tầng thứ ba trong mô hình OSI. Tầng này có trách nhiệm quản lý việc định tuyến và chuyển tiếp dữ liệu giữa các mạng khác nhau trong hệ thống mạng. Tầng Mạng cung cấp các dịch vụ cho tầng trên là tầng Giao vận và tầng dưới là tầng Liên kết dữ liệu.

![hinh_2.3](/LinhNH/CCNA/02.Timhieu_OSI/images/Network_Layer.png)
- Tầng Mạng là tầng quan trọng trong mô hình OSI, vì nó đảm bảo việc định tuyến và chuyển tiếp dữ liệu giữa các mạng khác nhau. Các chức năng quan trọng của tầng Mạng bao gồm:
  - __Định tuyến__ (Routing): Tầng Mạng xác định đường đi tốt nhất cho việc truyền gói tin từ nguồn đến đích qua các mạng khác nhau. Nó sử dụng các thuật toán định tuyến như RIP (Routing Information Protocol) và OSPF (Open Shortest Path First) để quyết định đường đi tối ưu.
  - __Chuyển tiếp__ (Forwarding): Tầng Mạng thực hiện chuyển tiếp gói tin từ đầu vào đến đầu ra thông qua các thiết bị định tuyến (router). Các thiết bị định tuyến sử dụng bảng định tuyến để xác định cách chuyển tiếp gói tin đến đích.
  - __Địa chỉ IP__ (IP Addressing): Tầng Mạng sử dụng địa chỉ IP để định danh và định vị các thiết bị trong mạng. Địa chỉ IP là một địa chỉ duy nhất cho mỗi thiết bị mạng và nó được sử dụng để xác định nguồn và đích của gói tin.
  - __Fragmentation và Reassembly__: Tầng Mạng có khả năng phân mảnh (fragmentation) gói tin thành các phần nhỏ hơn để truyền qua các mạng có độ dài giới hạn. Ngược lại, nó cũng có khả năng ghép (reassembly) các phần nhỏ thành gói tin ban đầu khi gói tin đến đích.

### 2.4 Tầng giao vận (Transport layer)
 - Tầng Giao vận là tầng thứ tư trong mô hình OSI, có trách nhiệm dữ liệu truyền đi là đáng tin cậy. Nó tạo điều kiện cho việc giao tiếp hiệu quả và đáng tin cậy giữa các ứng dụng, bất kể sử dụng các mạng hoặc thiết bị khác nhau.

![hinh_2.4](/LinhNH/CCNA/02.Timhieu_OSI/images/Transport_Layer.png)

 - Các chức năng quan trọng của tầng Giao vận bao gồm:

  - __Điều khiển luồng__ (Flow Control): Tầng Giao vận quản lý việc truyền dữ liệu giữa các ứng dụng và điều chỉnh tốc độ truyền để đảm bảo rằng không bị quá tải hoặc quá chậm so với nguồn tiêu thụ.
  - __Điều khiển lỗi__ (Error Control): Tầng Giao vận sử dụng các cơ chế kiểm soát lỗi như checksum và ACK/NACK để đảm bảo rằng dữ liệu được truyền một cách tin cậy và không bị lỗi.
  - __Đánh số gói__ (Segmentation/Reassembly): Tầng Giao vận chia nhỏ dữ liệu từ các ứng dụng thành các đơn vị gói tin (segment) và gắn số thứ tự vào mỗi gói. Khi nhận được, tầng Giao vận ghép các đơn vị gói lại thành dữ liệu ban đầu.
  - __Đa kết nối__ (Connection Multiplexing): Tầng Giao vận hỗ trợ việc thiết lập và duy trì các kết nối mạng đa kết nối (multi-connection), cho phép nhiều ứng dụng trên cùng một thiết bị mạng gửi và nhận dữ liệu đồng thời.

### 2.5 Tầng phiên (Session layer)
 - Tầng Phiên là tầng thứ năm trong mô hình mạng OSI . Tầng này có trách nhiệm thiết lập, duy trì và kết thúc các phiên (sessions) giao tiếp giữa các ứng dụng trên mạng. Nó tạo ra một môi trường nhất quán cho việc thiết lập và duy trì phiên giao tiếp, đồng bộ hóa dữ liệu và chấm dứt phiên.

![hinh_2.5](/LinhNH/CCNA/02.Timhieu_OSI/images/Session_Layer.png)

- Các chức năng quan trọng của tầng Phiên bao gồm:

  - __Thiết lập phiên__ (Session establishment): Tầng Phiên cho phép các ứng dụng thiết lập phiên giao tiếp giữa chúng trước khi truyền dữ liệu. Quá trình này bao gồm xác định và thiết lập các thông số phiên như các thông tin định danh, cấu hình và các thông tin điều khiển khác.
   - __Duy trì phiên__ (Session maintenance): Tầng Phiên đảm bảo việc duy trì và quản lý phiên giao tiếp giữa các ứng dụng. Nó kiểm soát việc truyền dữ liệu giữa các ứng dụng trong suốt thời gian phiên diễn ra, đồng bộ hóa dữ liệu và xử lý các yêu cầu và phản hồi.
  - __Đồng bộ phiên__ (Session synchronization): Tầng Phiên xác định các điểm đồng bộ trong quá trình truyền dữ liệu giữa các ứng dụng. Điều này đảm bảo rằng dữ liệu được truyền một cách nhất quán và đúng thứ tự giữa nguồn và đích.
   - __Chấm dứt phiên__ (Session termination): Tầng Phiên cho phép các ứng dụng kết thúc phiên giao tiếp một cách an toàn và đúng quy trình. Quá trình này bao gồm thông báo, truyền tải thông tin hoàn thành và giải phóng tài nguyên được sử dụng trong phiên.

### 2.6 Tầng trình diễn (Presentation layer)
- Tầng Trình diễn là tầng thứ sáu trong mô hình OSI. Tầng này đảm nhiệm vai trò chuyển đổi và xử lý dữ liệu từ định dạng của ứng dụng thành định dạng chuẩn để truyền qua mạng và ngược lại. Nó cung cấp các dịch vụ và các cơ chế chuyển đổi, mã hóa, nén và định dạng dữ liệu để đảm bảo rằng dữ liệu được truyền và nhận một cách chính xác, an toàn và hiệu quả.

![hinh_2.6](/LinhNH/CCNA/02.Timhieu_OSI/images/Presentation_Layer.png)

- Các chức năng chính của tầng Trình diễn bao gồm:
  - __Mã hóa/ Giải mã__ (Encryption/Decryption): Tầng Trình diễn có khả năng mã hóa dữ liệu trước khi truyền và giải mã dữ liệu khi nhận. Điều này đảm bảo tính bảo mật trong quá trình truyền dữ liệu trên mạng.
  - __Nén/ Giải nén__ (Compression/Decompression): Tầng Trình diễn có khả năng nén dữ liệu để giảm dung lượng truyền và giải nén dữ liệu khi nhận. Điều này giúp tăng tốc độ truyền dữ liệu và giảm sử dụng băng thông mạng.
  - __Định dạng dữ liệu__ (Data Formatting): Tầng Trình diễn thực hiện việc định dạng dữ liệu từ định dạng của ứng dụng thành định dạng chuẩn để truyền qua mạng và ngược lại. Điều này đảm bảo tính tương thích giữa các ứng dụng và hệ thống khác nhau.
  - __Quản lý phiên__ (Session Management): Tầng Trình diễn có khả năng quản lý các thông tin phiên giao tiếp giữa các ứng dụng. Nó hỗ trợ việc khởi tạo, duy trì và kết thúc phiên giao tiếp, đồng bộ hóa các hoạt động truyền dữ liệu và xử lý lỗi.

### 2.7 Tầng ứng dụng (Application layer)
- Tầng Ứng dụng (Application layer) là tầng cuối cùng và cao nhất trong mô hình OSI. Nó cung cấp giao diện giữa người dùng và mạng, cho phép người dùng truy cập vào các dịch vụ mạng và thực hiện các hoạt động liên quan đến ứng dụng.

![hinh_2.7](/LinhNH/CCNA/02.Timhieu_OSI/images/Application_Layer.png)

- Tầng Ứng dụng bao gồm nhiều giao thức và dịch vụ như truyền tệp, truyền thư điện tử (email), truyền dữ liệu web, truyền dữ liệu đa phương tiện và nhiều ứng dụng khác. Một số giao thức và dịch vụ phổ biến tại tầng này bao gồm:

  - HTTP (Hypertext Transfer Protocol).
  - FTP (File Transfer Protocol).
  - SMTP (Simple Mail Transfer Protocol).
  -  DNS (Domain Name System).
  - SNMP (Simple Network Management Protocol).
- Chức năng chính của tầng ứng dụng là cung cấp giao diện và các dịch vụ để người dùng có thể tương tác và sử dụng các ứng dụng mạng. Nó cung cấp các cơ chế để xác định và thiết lập kết nối với các ứng dụng và dịch vụ mạng, xử lý yêu cầu và phản hồi, quản lý phiên làm việc và truyền tải dữ liệu giữa người dùng và mạng.

 ***__Tổng kết__***

![hinh_2.7](/LinhNH/CCNA/02.Timhieu_OSI/images/Tong_ket.png)


## 3. Workflow với mô hình OSI
_Khi A gửi một dữ liệu (thông tin) đến B thì dữ liệu sẽ trải qua 2 tiến trình cơ bản là_

### Phía máy gửi: Quá trình đóng gói tại trạm gửi (Data Encapsulation)

![hinh_3.1](/LinhNH/CCNA/02.Timhieu_OSI/images/Phia_may_gui.png)

- __Bước 1__: Trình ứng dụng (bên A) tạo ra dữ liệu và các chương trình phần cứng, phần mềm cài đặt mỗi lớp sẽ bổ sung vào header
- __Bước 2__: Tiếp theo các thông tin đó được chuyển xuống lớp Presentation để chuyển thành dạng chung, rồi mã hoá và nén dữ liệu. Tiếp đó dữ liệu được chuyển xuống lớp Session để bổ sung các thông tin về phiên giao dịch này.
- __Bước 3__: Dữ liệu tiếp tục được chuyển xuống lớp Transport, tại đây dữ liệu được cắt ra thành nhiều Segment và dán số port đích, port source (ngẫu nhiên), số thứ tự vào mỗi phần nhỏ đó để đảm bảo độ tin cậy khi truyền.
- __Bước 4__: Dữ liệu tiếp tục được chuyển xuống lớp Network, tại lớp này mỗi Segment được cắt ra thành nhiều Packet và thực hiện việc tìm nexthop để đẩy gói tin đi.
- __Bước 5__: Tiếp đó dữ liệu được chuyển xuống lớp DataLink, tại đây thực hiện việc dán địa chỉ mac cổng thiết bị hiện tại và mac đích (mac của cổng router phía trước), dán xong thì packet được gọi là frame.
- __Bước 6__: Cuối cùng, mỗi Frame sẽ được tầng Vật Lý chuyển thành một chuỗi các bit và truyền đến B trên dây mạng.

### Phía máy nhận: Quá trình mở gói dữ liệu (Data De-encapsulation)

![hinh_3.2](/LinhNH/CCNA/02.Timhieu_OSI/images/Phia_may_nhan.png)

- __Bước 1__: Lớp Physical kiểm tra quá trình đồng bộ bit và đặt chuỗi bit nhận được vào vùng đệm. Sau đó thông báo cho lớp Data Link dữ liệu đã được nhận.
- __Bước 2__: Lớp DataLink kiểm lỗi frame. Nếu có lỗi thì frame bị bỏ. Sau đó kiểm tra địa chỉ lớp DataLink (địa chỉ mac) xem có trùng với địa chỉ máy nhận hay không. Nếu đúng thì phần dữ liệu sau khi loại header sẽ được chuyển lên cho lớp Network.
- __Bước 3__: Địa chỉ lớp Networkđược kiểm tra xem có phải là địa chỉ máy nhận hay không (địa chỉ IP) ? Nếu đúng thì dữ liệu được chuyển lên cho lớp Transport xử lý.
- __Bước 4__: Nếu giao thức lớp Transport có hỗ trợ việc phục hồi lỗi thì số định danh phân đoạn được xử lý. Các thông tin ACK,NAK (gói tin ACK,NAK dùng để phản hồi về việc các gói tin đã được gởi đến máy nhận chưa) cũng được xử lý ở lớp này. Sau quá trình phục hồi lỗi và sắp thứ tự các phân đoạn, dữ liệu được đưa lên lớp Session.
- __Bước 5__: Lớp Session đảm bảo một chuỗi các thông điệp đã trọn vẹn. Sau khi các luồng đã hoàn tất, lớp Session chuyển dữ liệu sau header lớp 5 lên cho lớp Presentation xử lý.
- __Bước 6__: Dữ liệu sẽ được lớp Presentation xử lý bằng cách chuyển đổi dạng thức dữ liệu. Sau đó kết quả chuyển lên cho lớp Application.
- __Bước 7__: Lớp Application xử lý header cuối cùng. Header này chứa các tham số thoả thuận giữa hai trình ứng dụng. Do vậy tham số này thường chỉ được trao đổi lúc khởi động quá trình truyền thông giữa hai trình ứng dụng.
------------




