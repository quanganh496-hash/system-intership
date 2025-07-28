# Tìm hiểu VLAN, Trunking
# Mục lục
1. [VLAN](#1-vlan)  
    1.1 [Tìm hiểu khái quát về vlan](#11-tìm-hiểu-khái-quát-về-vlan)  
    1.2 [Phân loại vlan](#12-phân-loại-vlan)  
    1.3 [Cách thức hoạt động VLAN](#13-cách-thức-hoạt-động)  
2. [Trunking](#2-trunking)  
    2.1 [Khái niệm ](#21-khái-niệm)  
    2.2 [Chuẩn trunking](#22-chuẩn-trunking)  
3. [Một số thiết bị khác](#3-một-số-thiết-bị-khác)  
    3.1 [Router](#31-router)  
    3.2 [Switch](#32-switch)  
    3.3 [Firewall](#33-firewall)  
    3.4 [Hub](#34-hub)  
    3.5 [Gateway](#35-gateway)

## 1. VLAN
### 1.1 Tìm hiểu khái quát về VLAN
![hinh_1](/LinhNH/05.Timhieu_VLAN_Trunking/images/VLAN.png)
- VLAN (Virtual Local Area Network) hay còn gọi là mạng LAN ảo. Mạng LAN ảo (VLAN) là một nhóm các máy tính được kết nối với cùng một mạng nhưng không ở gần nhau. Sử dụng VLAN cho phép sử dụng tài nguyên mạng hiệu quả hơn và có thể hữu ích khi có quá nhiều thiết bị cho một mạng. 
- Một VLAN được định nghĩa là một nhóm logic các thiết bị mạng và được thiết lập dựa trên các yếu tố như chức năng, bộ phận, ứng dụng… của công ty. Về mặt kỹ thuật, VLAN là một miền quảng bá được tạo bởi các switch. Bình thường thì router đóng vai trò tạo ra miền quảng bá. Đối với VLAN, switch có thể tạo ra miền quảng bá.  

___Khi nào bạn cần một VLAN ?___  
Bạn cần cân nhắc việc sử dụng VLAN trong các trường hợp sau đây:
- Bạn có hơn 200 máy tính trong mạng LAN
- Lưu lượng quảng bá (broadcast traffic) trong mạng LAN của bạn quá lớn
- Các nhóm làm việc cần gia tăng bảo mật hoặc bị làm chậm vì quá nhiều bản tin quảng bá.
- Các nhóm làm việc cần nằm trên cùng một miền quảng bá vì họ đang dùng chung các ứng dụng.
- Hoặc chỉ để chuyển đổi một switch đơn thành nhiều switch ảo.
### 1.2. Phân loại VLAN   
Có 3 loại VLAN, bao gồm:  
- > Port - based VLAN   

Là cách cấu hình VLAN đơn giản và phổ biến. Mỗi cổng của Switch được gắn với một VLAN xác định (mặc định là VLAN 1), do vậy bất cứ thiết bị host nào gắn vào cổng đó đều thuộc một VLAN nào đó.
- > MAC address based VLAN

Cách cấu hình này ít được sử dụng do có nhiều bất tiện trong việc quản lý. Mỗi địa chỉ MAC được đánh dấu với một VLAN xác định.
- >Protocol – based VLAN: 

Cách cấu hình này gần giống như MAC Address based, nhưng sử dụng một địa chỉ logic hay địa chỉ IP thay thế cho địa chỉ MAC. Cách cấu hình không còn thông dụng nhờ sử dụng giao thức DHCP.

### 1.3. Cách thức hoạt động  
![hinh_3](/LinhNH/05.Timhieu_VLAN_Trunking/images/cach-hoat-dong.png)

Một VLAN được xác định trên các switch bằng một ID VLAN. Mỗi cổng trên một switch sẽ được gán cho một hoặc nhiều VLAN ID, trường hợp không được chỉ định thì nó sẽ được chuyển tới một VLAN mặc định. Mỗi VLAN sẽ cung cấp quyền truy cập dữ liệu cho tất cả những thiết bị kết nối với cổng trên switch phù hợp với VLAN ID của nó.

ID VLAN sẽ được dịch sang thẻ VLAN bằng một thẻ 12 bit xác định tối đa 4.096 VLAN trên mỗi miền chuyển mạch. IEEE sẽ chịu trách nhiệm gắn thẻ VLAN theo tiêu chuẩn 802.1Q. Switch sẽ thêm thẻ VLAN cho khung Ethernet. Với Static VLAN, switch sẽ chèn thẻ được liên kết với ID VLAN của cổng nhập. Riêng Dynamic VLAN, switch sẽ chèn thẻ được liên kết với ID của thiết bị đó hoặc loại lưu lượng mà nó tạo ra.

Các khung Ethernet được gắn thẻ sẽ chuyển tiếp về địa chỉ MAC đích của chúng (chỉ chuyển tiếp đến các cổng có liên kết VLAN). Lưu lượng quảng bá (broadcast), unicast, multicast đều được chuyển tiếp đến các cổng trong VLAN.

Đường trung kế kết nối (Trunk) giữa các switch nhận biết được VLAN nào trải dài trên switch. Trunk còn đóng vai trò truyền lưu lượng truy cập cho các VLAN được sử dụng ở hai phía đầu, cuối của nó. Khi một khung chạm đến switch đích thì thẻ VLAN sẽ bị xóa trước khi khung được truyền tới máy tính đích.

Spanning Tree Protocol ( STP )là một giao thức được dùng để ngăn chặn sự lặp vòng giữa các switch trong mỗi miền lớp 2 (Ethernet). Mỗi VLAN sẽ chạy một STP riêng biệt, không phụ thuộc lẫn nhau. Nếu cấu trúc liên kết giữa nhiều VLAN giống nhau thì có thể chạy STP đa trường hợp để giảm chi phí STP.

## 2. Trunking
### 2.1 Khái niệm
`Đường Trunk hay Trunking` là một kỹ thuật kết nối các thiết bị mạng với nhau để tạo thành một mạng lớn hơn, đặc biệt trong các mạng LAN hoặc các mạng VLAN. Đường trunk cho phép chuyển gói dữ liệu từ một VLAN này sang một VLAN khác trên cùng một đường truyền vật lý, điều này giúp tối ưu hóa việc sử dụng băng thông và giảm độ trễ trong mạng.
### 2.2 Chuẩn Trunking

> a. IEEE 802.1Q  

![hinh_2a](/LinhNH/05.Timhieu_VLAN_Trunking/images/chuan-dot1q.png)
___`HOẠT ĐỘNG`___  
Khi switch nhận được Frame có tag thông tin 802.1Q, nó sẽ tiến hành đọc thông tin này, xem frame này đến từ VLAN nào. Sau đó  xử lí gở bỏ Tag trả lại frame đúng VLAN mà frame thuộc về. Thực chất Tag DOT1Q chỉ được tag trên đường trunk để phân biệt các frame của các VLAN khác nhau. Các End users không nhận biết được rằng frame được Tag và chuyển trên đường trunk. Trunking hoàn toàn riêng biệt với các thiết bị đầu cuối này.

![hinh_2b](/LinhNH/05.Timhieu_VLAN_Trunking/images/chuan-isl.png)
___`ISL Header`___   
Header của ISL có chứa nhiều trường với các giá trị xác định thuộc tính của dữ liệu frame nguồn. Thông tin này được sử dụng để giao nhận, nhận dạng đường truyền, và nhận dạng VLAN. Độ lớn của các trường trong header ISL khác nhau, tùy thuộc vào loại VLAN và loại đường liên kết. Các ASIC trên một cổng Ethernet đóng gói các frame với một header ISL 26 byte và một FCS 4 byte. Đây là 30-byte mà ISL đóng gói bổ sung thêm đã được hỗ trợ trong giao thức của Switch Cisco, nhưng kích thước tổng thể của frame thay đổi và được giới hạn bởi các MTU của giao thức lớp 2. 


## 3. Một số thiết bị khác
### 3.1 Router
`Khái niệm` 
Router (thiết bị định tuyến hoặc bộ định tuyến) là thiết bị mạng dùng để chuyển đổi các gói dữ liệu đến các thiết bị đầu cuối. Về cơ bản, router là một thiết bị để chia sẻ internet tới nhiều các thiết bị khác trong cùng lớp mạng.

![hinh_3.1](/LinhNH/05.Timhieu_VLAN_Trunking/images/cautao-router-wifi.png)

`Cấu tạo`  
- Cổng mạng LAN   
Là mạng cục bộ (có thể có 1 hoặc nhiều cổng mạng LAN). Hiện nay thường các Router đều có 2 cổng LAN trở lên giúp kết nối từ modem chính đến các thiết bị đầu cuối (tivi, laptop, máy tính,…) để sử dụng mạng internet thông qua cáp mạng. Trên thị trường cổng LAN cũng rất đa dạng với nhiều tốc độ khác nhau đáp ứng được độ truyền tải cao và nhanh chóng.
    
- Cổng WAN  
Là mạng diện rộng (có 1 hoặc 2) nhưng thường sử dụng là 1, nhưng đối với một số Router chuyên dùng thì sẽ có 2 cổng WAN. Cổng Wan nằm ở mặt sau Router, được sử dụng để kết nối với modem để truy cập internet từ nhà cung cấp ISP để tận dụng lợi thế của mạng internet trên tất cả các thiết bị được kết hợp với nó.

- Anten  
Loại phát sóng wifi có thể là anten ngoài hoặc ăngten ngầm. Hiện nay, phổ biến thường là anten ngoài, số lượng anten càng nhiều thì càng tăng cường độ phát sóng Wifi hơn.  

    Ngoài ra, cấu tạo Router còn có cổng cắm điện và một số nút chuyên dụng, đèn tín hiệu,...

`Chức năng`  
Router có chức năng gửi các gói dữ liệu mạng giữa 2 hoặc nhiều mạng, từ một tới nhiều điểm đích đến cuối cùng từ router.

`Các loại router`
- Wired router (router có dây)
- Wireless router (Router không dây)
- Virtual router (Router ảo) 

### 3.2 Switch
`Khái quát`  
Switch hay switch mạng là thiết bị chuyển mạch hay bộ chuyển mạch. Đây là một thiết bị chuyển mạch vô cùng quan trong hệ thống mạng có khả năng kết nối các đoạn mạch với nhau theo mô hình sao (Star), giúp gửi nhận thông tin và tài nguyên 1 cách hiệu quả, trơn tru, bảo mật cao. 

![hinh_3.2](/LinhNH/05.Timhieu_VLAN_Trunking/images/switch.png)
Hiểu một cách đơn giản nhất thì switch giống như một thiết bị trung tâm, tất cả các thiết bị đầu cuối End sử dụng mạng khác nằm trong cùng 1 hệ thống mạng với switch như: máy tính, máy quét, máy in,... đều được kết nối với thiết bị này để có thể giao tiếp, truyền nhận dữ liệu.

Switch là thiết bị mạng chính của nhiều hệ thống mạng doanh nghiệp, giúp kết nối nhiều thiết bị đầu cuối như máy tính, máy in, điện thoại, đèn, máy chủ server và phần cứng khác.  
`Cấu tạo`  
Một switch mạng sẽ có cấu tạo gồm 2 phần bao gồm: Phần cứng và phần mềm:   
- Phần cứng hardware: gồm khung vỏ thiết bị (vỏ nhựa hoặc vỏ sắt), nguồn điện cấp, ở bên trong có các linh kiện mạch bên trong (CPU, bộ nhớ, bo mạch chủ, các Bus hệ thống), các cổng kết nối ngoại vi (4 port, 8 port, 16 port, 24 port, 48 port,…).
- Phần mềm software: các thuật toán đã được cài đặt sẵn, phần mềm thiết bị switch sử dụng hệ điều hành OS.

**`Switch Layer 2`** truy xuất cập nhật địa chỉ MAC có trong frame, cho phép các thiết bị có thể truyền tin nhanh chóng cho nhau mà không cần phải kết nối trực tiếp.  
Điểm đặc biệt là switch Layer 2 :  
- Không cần chia sẻ băng thông nhưng vẫn truyền dữ liệu một cách nhanh chóng.
- Có khả năng điều chỉnh giới hạn của lưu lượng trưởng ở ngưỡng nào đó.
- Switch Layer 2 còn có khả năng tạo ra mạng ảo VLAN sẽ tối ưu các nhóm trong mạng một cách dễ dàng.  

**`Switch layer 3`** bao gồm nhiều tính năng hơn Switch Layer 2. Sở dĩ như vậy là bởi vì một số dịch vụ trong đó làm cho switch layer 3 hoạt động tốt hơn switch layer 2 như: bảng CAM, bảng FIB, địa chỉ IP của next hop, địa chỉ MAC,… Chính vì vậy giá thành của switch Layer 3 cao hơn hẳn switch Layer 2.

Hơn nữa, hoạt động của switch layer 3 không những sở hữu các tính năng của Switch layer 2 mà còn tham gia vào một số hoạt động dựa trên thông tin của layer 3 và layer 4.  
Điểm đặc biệt là Switch Layer 3:
- Có thể lưu bảng của địa chỉ MAC của thiết bị kết nối.
- Có thêm bảng định tuyến của một Router.

![hinh_3.2.1](/LinhNH/05.Timhieu_VLAN_Trunking/images/switch-layer-2-3.png)

### 3.3 Firewall
`Khái quát`  
FireWall là một kỹ thuật được tích hợp vào hệ thống mạng để chống lại sự truy cập trái phép nhằm bảo vệ các nguồn thông tin nội bộ cũng như hạn chế sự xâm nhập vào hệ thông của một số thông tin khác không mong muốn.

![hinh](/LinhNH/05.Timhieu_VLAN_Trunking/images/firewall.png)


Internet FireWall là một tập hợp thiết bị (bao gồm phần cứng và phần mềm) giữa mạng của một tổ chức, một công ty, hay một quốc gia và Internet.

`Cấu trúc của FireWall`

FireWall bao gồm : Một hoặc nhiều hệ thống máy chủ kết nối với các bộ định tuyến (router) hoặc có chức năng router.

Các phần mềm quản lí an ninh chạy trên hệ thống máy chủ. Thông thường là các hệ quản trị xác thực (Authentication), cấp quyền (Authorization) và kế toán (Accounting).

`Các thành phần của FireWall`

Một FireWall bao gồm một hay nhiều thành phần sau :
+ Bộ lọc packet (packet- filtering router).
+ Cổng ứng dụng (Application-level gateway hay proxy server).
+ Cổng mạch (Circuite level gateway).

`Chức năng`  
FireWall quyết định những dịch vụ nào từ bên trong được phép truy cập từ bên ngoài, những người nào từ bên ngoài được phép truy cập đến các dịch vụ bên trong, và cả những dịch vụ nào bên ngoài được phép truy cập bởi những người bên trong.

### 3.4 Hub
Hub là thiết bị mạng cơ bản nhất kết nối nhiều PC hoặc kết nối các thiết bị mạng khác với nhau. Không giống như bộ chuyển mạch Switch hoặc bộ định tuyến Router, Hub không có bảng định tuyến hoặc thông tin về nơi gửi và phát tất cả dữ liệu mạng trên mỗi kết nối.

Hub và Switch đóng vai trò như một kết nối trung tâm với tất cả các thiết bị mạng của bạn và xử lý một kiểu dữ liệu gọi là khung. Khi nhận được một khung, nó được khuếch đại và sau đó truyền đến cổng của máy tính đích.

Trong một bộ tập trung Hub, một Frame được truyền đi hoặc “broadcast” tới tất cả các cổng của nó. Hub không có cách nào phân biệt cổng nào sẽ được gửi đến. Chuyển nó đến tất cả các cổng đảm bảo rằng nó sẽ đạt đến đích dự kiến của nó. Điểm này đặt rất nhiều lưu lượng truy cập trên mạng và có thể dẫn đến thời gian phản hồi mạng kém.
Hub sở hữu nhiều cổng từ 4 lên tới 24 cổng, và được coi như là một Repeater nhiều cổng. Khi thông tin được truyền tín hiệu vào một cổng của Hub, các cổng khác cũng sẽ nhận được thông tin ngay lập tức.   
Hiện nay có 2 loại Hub phổ biến là Active Hub và Smart Hub:

- Active Hub: loại Hub này thường được dùng phổ biến hơn rất nhiều, cần được cấp nguồn khi hoạt động. Active Hub dùng để khuếch đại tín hiện đến và chia ra những cổng còn lại để đảm bảo tốc độ tín hiệu cần thiết khi sử dụng. 
- Smart Hub: nó cũng có chức năng làm việc tương tự như Active Hub, nhưng được tích hợp thêm chip có khả năng tự động kiểm tra lỗi trên mạng.

So với switch, hub chậm hơn vì nó có thể gửi hoặc nhận thông tin không chỉ cùng một lúc, mà tốn nhiều hơn một hub.

### 3.5 Gateway
Chức năng chính của thiết bị Gateway là kết nối các máy tính với nhau một cách dễ dàng ngay cả khi những thiết bị này không sử dụng chung một giao thức.
Ví dụ như Gateway có thể kết nối máy tính sử dụng giao thức IP với máy tính sử dụng giao thức SNA, IPX... Ngoài ra thiết bị này còn có khả năng phân biệt các giao thức. Vì vậy thường được ứng dụng trong việc chuyển thư điện tử từ mạng này sang mạng khác kể cả đường truyền xa. 

