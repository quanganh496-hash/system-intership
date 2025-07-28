# Tìm hiểu về VLAN, trunking

## 1.VLAN

VLAN (Virtual Local Area Network) là mạng LAN ảo được hình thành từ một hay nhiều mạng LAN cho phép nhóm các thiết bị khả dụng kết nối cùng với một mạng dù không đặt cạnh nhau.

![image1](/HoangNH/5.TimhieuVlan/image/vlan.png)

Cách thức hoạt động:

Một VLAN được xác định trên các switch bằng một ID VLAN. Mỗi cổng trên một switch sẽ được gán cho một hoặc nhiều VLAN ID, trường hợp không được chỉ định thì nó sẽ được chuyển tới một VLAN mặc định. Mỗi VLAN sẽ cung cấp quyền truy cập dữ liệu cho tất cả những thiết bị kết nối với cổng trên switch phù hợp với VLAN ID của nó.

ID VLAN sẽ được dịch sang thẻ VLAN bằng một thẻ 12 bit xác định tối đa 4.096 VLAN trên mỗi miền chuyển mạch. IEEE sẽ chịu trách nhiệm gắn thẻ VLAN theo tiêu chuẩn 802.1Q. Switch sẽ thêm thẻ VLAN cho khung Ethernet. Với Static VLAN, switch sẽ chèn thẻ được liên kết với ID VLAN của cổng nhập. Riêng Dynamic VLAN, switch sẽ chèn thẻ được liên kết với ID của thiết bị đó hoặc loại lưu lượng mà nó tạo ra.

Các khung Ethernet được gắn thẻ sẽ chuyển tiếp về địa chỉ MAC đích của chúng (chỉ chuyển tiếp đến các cổng có liên kết VLAN). Lưu lượng quảng bá (broadcast), unicast, multicast đều được chuyển tiếp đến các cổng trong VLAN.

Đường trung kế kết nối (Trunk) giữa các switch nhận biết được VLAN nào trải dài trên switch. Truck còn đóng vai trò truyền lưu lượng truy cập cho các VLAN được sử dụng ở hai phía đầu, cuối của nó. Khi một khung chạm đến switch đích thì thẻ VLAN sẽ bị xóa trước khi khung được truyền tới máy tính đích.

Spanning Tree Protocol ( STP )là một giao thức được dùng để ngăn chặn sự lặp vòng giữa các switch trong mỗi miền lớp 2 (Ethernet). Mỗi VLAN sẽ chạy một STP riêng biệt, không phụ thuộc lẫn nhau. Nếu cấu trúc liên kết giữa nhiều VLAN giống nhau thì có thể chạy STP đa trường hợp để giảm chi phí STP.

Phân biệt Access port và Trunking port

- Access port: được cấu hình để thuộc về VLAN cụ thể. cung cấp liên kết chuyên dụng đến máy chủ, bộ định tuyến hoặc thiết bị đầu cuối trong một Vlan duy nhất. chỉ truyền tải lưu lượng dữ liệu phù hợp với giá trị truy cập của VLAN được gán trước. Các cổng truy cập không gắn thẻ (untagged), nghĩa là khi dữ liệu ra khỏi cổng, nó không được gắn thêm thông tin về VLAN.
- Trunking port: chuyển dữ liệu của nhiều VLAN khác nhau trên qua cùng một kết nối vật lý. Cổng trunk gắn thẻ (tagged) dữ liệu với các thẻ VLAN để cho phép các thiết bị khác biết dữ liệu thuộc về VLAN nào.

![image2](/HoangNH/5.TimhieuVlan/image/trunk.jpg)

## 2.Trunking

Đường Trunk hay Trunking là một kỹ thuật kết nối các thiết bị mạng với nhau để tạo thành một mạng lớn hơn, đặc biệt trong các mạng LAN hoặc các mạng VLAN. Đường trunk cho phép chuyển gói dữ liệu từ một VLAN này sang một VLAN khác trên cùng một đường truyền vật lý, điều này giúp tối ưu hóa việc sử dụng băng thông và giảm độ trễ trong mạng.

VLAN Trunk là đường dây kết nối dữ liệu từ các mạng VLAN ở các tầng với nhau. Tuy nhiên VLAN Trunk cho phép bạn chỉ cần sử dụng 1 đường dây kết nối dữ liệu duy nhất giữa các mạng VLAN với nhau thay vì phải trang bị từng dây cáp mạng nối riêng biệt tương ứng giữa các mạng VLAN ảo.

VLAN Trunk sử dụng các giao thức đặc biệt như IEEE 802.1Q để đánh dấu dữ liệu của từng VLAN và giúp các thiết bị trong mạng hiểu cách truyền dữ liệu giữa các VLAN.

VLAN Trunk cho phép các thiết bị mạng như switch, router hoặc máy chủ, truyền dữ liệu của nhiều VLAN thông qua cùng một kết nối vật lý. 
Khi dữ liệu từ các VLAN khác nhau được gửi tới cổng Trunk trên một thiết bị mạng, nó được đánh dấu (tagged) bằng các thẻ (tag) định danh cho VLAN nguồn của nó. Điều này cho phép các thiết bị khác nhận biết và xử lý dữ liệu đúng cách, đảm bảo dữ liệu được gửi tới VLAN mục tiêu mà không bị trộn lẫn với các VLAN khác.

### 2.1.Các chuẩn trunking cho một hệ thống mạng

#### 2.1.1.Chuẩn IEEE và kỹ thuật DOT1Q

Kỹ thuật trunking DOT1Q thực hiện chèn thêm 4 byte vào sau trường Source MAC của Ethernet Frame trên đường trunk. Thông tin chèn này được gọi là DOT1Q Tag.

![image3](/HoangNH/5.TimhieuVlan/image/dot1q.jpg)

Các trường trong 802.1Q VLAN Tag bao gồm:

- Tag Protocol ID (16 bit) nôi dung trường này luôn được set 0x8100 dùng để định danh ra frame này đã đc tag 802.1q để phân biệt với frame untagged trên đường trunk.
- User Priority (3 bit) sử dụng cho kỹ thuật QoS.
- Canonical Format Indicator (1 bit) cho biết địa chỉ MAC đang được sử dụng ở định dạng Token Ring hay Ethernet Frame.
- VLAN ID(12 bit): cho biết Frame đang chạy trên đường trunk là của VLAN nào.

Cách xử lý frame:

Khi switch nhận được Frame có tag thông tin 802.1Q, nó sẻ tiến hành đọc thông tin này, xem frame này đến từ VLAN nào. Sau đó nó sẻ xử lí gở bỏ Tag trả lại frame đúng VLAN mà frame thuộc về. Thực chất Tag DOT1Q chỉ được tag trên đường trunk để phân biệt các frame của các VLAN khác nhau. Các End users không nhận biết được rằng frame được Tag và chuyển trên đường trunk. Trunking hoàn toàn transparent với các thiết bị đầu cuối này.

#### 2.1.2.Chuẩn CISCO và kỹ thuật trunking ISL 

Kỹ thuật Trunking này của Cisco tiến hành chèn thêm Header 26 byte và trường CRC kiểm tra lỗi 4 byte vào Ethernet Frame.

![image4](/HoangNH/5.TimhieuVlan/image/isl.jpg)

Các trường trong môt ISL Tag bao gồm:

- DA(Destination Address): 40 bit sẻ set ở dạng 0x01-00-0C-00-00″ or “0x03-00-0c-00-00”. Để báo hiệu bên nhận rằng frame được tag ở dạng ISL.
- Type: 4 bit chỉ ra type frame được và sử dụng là gì (0000:Ethernet, 0001: Token ring….).
- User: 4 bit chỉ ra độ ưu tiên của frame khi đi qua switch(XX00: normal priority, XX01: priority 1, XX10: priority 2, XX11: highest priority).
- SA(Source Address): 48 bit địa chỉ nguồn của gói tin ISL. Tuy nhiên thiết bị nhận có thể bỏ qua địa chỉ này
- LEN(Length): 16 bit cho biết kích thước của gói tin thực tế.
- AAAA03 là một giá trị 24 bit liên tục của  0xAAAA03.
- HSA(High Bits of Source Address):24 bit trường này chứa giá trị “0x00-00-0C.
- BPDU: được set để tất cả gói tin BPDU được tag ISL(hoạt động trên STP).
- INDEX: 16 bit chỉ ra chỉ số port nguồn của gói tin tồn tại trên Switch.
- RES: dài 16 bit sử dụng khi Token ring hoặc FDDI được đóng gói frame ISL, với frame Ethernet trường RES được set tất cả bit 0.


### 2.2.VTP

Giao thức đồng bộ thông tin VLAN giữa các thiết bị Switch của Cisco. Khi một hệ thống lớn thì việc tạo, xóa, sửa VLAN trong các Switch trở nên cực kì khó khăn. Thiếu tính chính xác và mất nhiều thời gian. Cisco đưa ra giao thức VTP tiến hành đồng bộ thông tin và cấu hình VLAN giữa các Switch trong cùng một miền Domain.
Các đặc điểm và cách thức hoạt động của VTP:
- VTP hoạt động trên các đường Trunking Layer 2 để trao đổi thông tin VLAN với nhau.
- 3 yếu tố quan trọng của VTP là : VTP domain, VTP password, VTP mode(Server, Client, Transparent). Trong đó
VTP domain : các switch được tổ chức cùng thuộc một domain mới có thể chia sẻ thông tin VLAN với nhau. Được thiết lập tĩnh trên các Switch.

VTP mode và đặc điểm các mode:
- Server : switch hoạt động ở mode này có toàn quyền quyết định tạo, xóa, sửa thông tin VLAN. Đồng bộ thông tin VLAN từ các Switch khác, Forward thông tin VLAN đến các Switch khác.
- Client: switch hoạt động ở mode này không được thay đổi thông tin VLAN mà chỉ nhận thông tin VLAN từ Server. Đồng bộ thông tin VLAN từ switch khác và forward thông tin VLAN.
- Transparent: switch hoạt động ở mode này không tiến hành tiếp nhận thông tin VLAN. Nó vẫn nhận được thông tin VLAN từ các Switch khác nhưng không tiến hành đồng bộ thông tin VLAN. Có thể tạo, xóa, sửa VLAN độc lập trên nó. Không gửi thông tin VLAN của bản thân cho các Switch khác nhưng nó có thể forward thông tin VLAN nhận được đến các Switch khác.

![image5](/HoangNH/5.TimhieuVlan/image/vtp.PNG)

## 3.Các thiết bị mạng

### 3.1.Router

Router là thiết bị mạng có chức năng chuyển tiếp dữ liệu giữa các mạng máy tính.
Router quản lý lưu lượng các mạng bằng cách chuyển tiếp gói dữ liệu đến địa chỉ IP đích và cho phép nhiều thiết bị sử dụng cùng một kết nối Internet.

Cấu tạo của router:

- Cổng WAN: thường có một cổng port WAN ở phía sau router, giúp cung cấp lớp mạng riêng và dải IP Default Gateway.
- Cổng LAN: có 2 cổng LAN trở lên, là cổng port kết nối mạng mà người dùng có thể kết nối trực tiếp từ router tới tivi, laptop,... thông qua dây cáp mạng Ethernet.
- Ăngten: Một router wifi sẽ có 2 loại ăngten là ăngten ngầm và ăngten ngoài. Ăngten ngầm sẽ giúp bộ router trông gọn gàng và đẹp mắt hơn, nhưng ăngten bên ngoài sẽ phát tín hiệu mạnh hơn.

### 3.2.Switch

Switch là thiết bị chuyển mạch có khả năng kết nối các đoạn mạch với nhau theo mô hình sao giúp gửi nhận thông tin và tài nguyên một cách hiệu quả, trơn tru, bảo mật cao.

Switch giống như một thiết bị trung tâm các thiết bị trong cùng một mạng với switch như máy tính, máy in... đều được kết nối với switch để giao tiếp, truyền nhận dữ liệu.

Switch Layer 2 là thiết bị chuyển mạch hoạt động ở tầng Data link trong mô hình OSI.
Switch Layer 2 sẽ thực hiện nhiệm vụ chuyển mạch và sử dụng địa chỉ MAC để xác định đường dẫn thông qua nơi các khung sẽ được chuyển tiếp và góp phần thực hiện nhiệm vụ truyền dữ liệu giữa các nút mạng kề nhau trong một mạng diện rộng hoặc giữa các nút trong cùng một segment mạng cục bộ.
Switch Layer 2 là một cầu nối trong suốt (transparent bridging) đi kèm với nhiều port. Mỗi port là một đoạn trong Ethernet của hệ thống mạng LAN, và luôn biệt lập với những port còn lại. 

Hoạt động của Switch hoàn toàn dựa theo địa chỉ MAC chứa trong gói tin, bởi vậy việc truyền tin sẽ không thể diễn ra khi chưa biết địa chỉ gốc.

Switch Layer 3 là thiết bị kết hợp chức năng của switch và router.
Switch Layer 3 là thiết bị chuyển mạch hoạt động như một công tắc để kết nối các thiết bị trong cùng một hệ thống mạng LAN ảo (VLAN), hỗ trợ thực hiện các giao thức định tuyến như kiểm tra gói thông tin, luân chuyển hoặc đưa ra những quyết định định tuyến dựa trên các địa chỉ nguồn và đích được chỉ định sẵn.

### 3.3.Repeater

Repeater là thiết bị khuếch đại, khuếch tán giúp đường truyền tín hiệu mạng đi xa ổn định hơn.

Có hai loại là LAN Repeater và Wifi Repeater.

### 3.4.Firewall

Firewall là một hệ thống an ninh mạng, có thể dựa trên phần cứng hoặc phần mềm sử dụng các quy tắc để kiểm soát lưu lượng vào ra của hệ thống.

Nó có thể được sử dụng để bảo vệ mạng khỏi các cuộc tấn công từ bên ngoài, chẳng hạn như tấn công từ mạng Internet, hay để ngăn chặn các cuộc tấn công từ bên trong mạng, chẳng hạn như các cuộc tấn công từ các máy tính bị nhiễm độc.

Khi lưu lượng mạng đi qua tường lửa, nó sẽ được kiểm tra và đánh giá để xác định liệu nó có phù hợp với các quy tắc bảo mật được cấu hình hay không. Nếu lưu lượng mạng không đáp ứng các quy tắc bảo mật, tường lửa sẽ chặn nó để ngăn chặn các cuộc tấn công mạng.

Tường lửa có thể kiểm soát lưu lượng mạng dựa trên một số yếu tố như địa chỉ IP, cổng mạng, giao thức và các luật quy định khác.

### 3.5.Hub

Hub là một thiết bị mạng được sử dụng để kết nối các máy tính hoặc các thiết bị khác trên cùng một mạng cục bộ LAN với nhau. Một hub sẽ bao gồm một số cổng port nhất định, thường từ 4 - 24 cổng, nhưng cũng có những hub có nhiều cổng hơn phụ thuộc vào người dùng.

Hub đóng vai trò như một điểm trung tâm kết nối các thiết bị trong hệ thống mạng và nếu một gói chỉ được truyền đến một cổng, nó sẽ được sao chép và truyền đến các cổng khác có thể nhận ra định dạng của gói tin.

Không giống như bộ chuyển đổi mạng và bộ định tuyến, hub sẽ không được thiết kế bảng định tuyến thông minh đến nơi gửi dữ liệu mà thay vào đó, hub sẽ phát hầu hết các dữ liệu trên mỗi cổng được kết nối. Tuy nhiên điều này cũng tạo ra rủi ro bảo mật dữ liệu. 

### 3.6.Gateway

Gateway là bộ chuyển đổi giao thức, được dùng để kết nối hai mạng có giao thức khác nhau, dữ liệu sẽ được giao tiếp đi qua Gateway trước khi định tuyến.

Gateway là một điểm giao tiếp giữa hai mạng khác nhau, nó có thể phân phối lưu lượng mạng giữa các mạng, định tuyến gói tin và thực hiện các chức năng bảo mật như tường lửa. Gateway có thể được triển khai dưới dạng phần cứng hoặc phần mềm và có thể được sử dụng trong nhiều ngữ cảnh khác nhau, từ mạng doanh nghiệp đến mạng gia đình.

### 3.7.Bridge

Bridge là một thiết bị dùng để kết nối nhiều mạng LAN cục bộ tạo thành một mạng LAN lớn hơn, bản chất bridge chính là lớp liên kết mạng cục bộ LAN. Chức năng này còn được gọi là cầu nối mạng, kiểm tra lưu lượng đến, xác định nên lọc lưu lượng hay chuyển tiếp lưu lượng đó đi.

