# Tìm hiểu về Routing, Static Routing
## Mục lục
1. [Routing](#1-tìm-hiểu-về-routing)  
    1.1 [Định tuyến](#11-định-tuyến-là-gì)  
    1.2 [Bộ định tuyến](#12-bộ-định-tuyến-là-gì)  
    1.3 [Cách hoạt động](#13-hoạt-động-của-định-tuyến)  
    1.4 [Phân loại](#14-phân-loại-định-tuyến)  
    1.5 [Thuật toán](#15-thuật-toán-định-tuyến)      
2. [Static Routing](#2-tìm-hiểu-về-static-routing)

------------------
## 1. Tìm hiểu về Routing

### 1.1 Định tuyến là gì?

![hinh_1.4](/LinhNH/06.Timhieu_Routing/images/khaiquat.png)


- Định tuyến là phương thức mà router (bộ định tuyến) hay pc (thiết bị mạng) dùng để chuyển các gói tin đến địa chỉ đích một cách tốt nhất (nghĩa là chỉ ra hướng và đường đi tốt nhất cho gói tin).

- Thông tin về những con đường này có thể được cập nhật tự động từ các router khác hoặc là do người quản trị mạng chỉ định cho router. Sau khi router nhận gói tin, thì router sẽ gỡ bỏ phần header lớp 2 để tìm địa chỉ đích thuộc lớp 3. Sau khi đọc xong địa chỉ đích lớp 3 nó tìm kiếm trong Routing Table cho mạng chứa địa chỉ đích.


Bảng định tuyến của mỗi giao thức định tuyến là khác nhau, nhưng có thể bao gồm những thông tin sau:

- Địa chỉ đích của mạng, mạng con hoặc hệ thống.

- Địa chỉ IP của router chặng kế tiếp phải đến.

- Giao tiếp vật lí phải sử dụng để đi đến Router kế tiếp.

- Subnet mask của địa chỉ đích.

- Khoảng cách đến đích (ví dụ: số lượng chặng để đến đích).

- Thời gian (tính theo giây) từ khi Router cập nhật lần cuối.


### 1.2 Bộ định tuyến là gì?

_Bộ định tuyến là một thiết bị mạng kết nối các thiết bị máy tính và mạng với những mạng khác. Các bộ định tuyến chủ yếu đảm nhận ba chức năng chính:_

- Xác định đường dẫn

Bộ định tuyến xác định đường dẫn mà dữ liệu sẽ đi khi dữ liệu di chuyển từ nguồn đến điểm đích. Bộ định tuyến cố gắng tìm đường dẫn tốt nhất bằng cách phân tích các chỉ số mạng như độ trì hoãn, dung lượng và tốc độ.

- Chuyển tiếp dữ liệu

Bộ định tuyến chuyển tiếp dữ liệu đến thiết bị tiếp theo trên đường dẫn đã chọn để cuối cùng là đến điểm đích của nó. Thiết bị và bộ định tuyến có thể nằm trên cùng một mạng hoặc trên các mạng khác nhau.

- Cân bằng tải

Đôi khi, bộ định tuyến có thể gửi bản sao của cùng một gói dữ liệu bằng cách sử dụng nhiều đường dẫn khác nhau. Bộ định tuyến làm thế này để giảm lỗi do tổn thất dữ liệu, tạo khả năng dự phòng và quản lý lưu lượng truy cập. 

### 1.3 Hoạt động của định tuyến

![hinh_1.3](/LinhNH/06.Timhieu_Routing/images/hoatdong.png)


- Khi gửi đi một gói dữ liệu từ một máy tính này sang một máy tính khác, đầu tiên quá trình sẽ xác định xem gói dữ liệu được gửi nội bộ đến máy tính khác trên cùng LAN hay đến Router để định tuyến đến LAN đích.

- Nếu gói dữ liệu được gửi đến một máy tính nằm trong một LAN khác, nó sẽ được gửi đến Router (hoặc gateway). Sau đó Router sẽ xác định tuyến khả thi nhất để chuyển tiếp dữ liệu theo tuyến đó. Gói dữ liệu sẽ được gửi đến Router tiếp theo và quá trình như vậy được lặp lại cho tới khi nó đến được LAN đích.

- Ở Lan đích, Router đích sẽ chuyển tiếp gói dữ liệu này đến máy tính đích. Để xác định xem tuyến nào là tốt nhất, các Router sử dụng thuật toán định tuyến phức tạp, thuật toán này sử dụng một loạt các hệ số gồm có tốc độ của môi trường truyền dẫn, số đoạn mạng và đoạn mạng có khả năng chuyển tải lưu lượng ở mức độ tối thiểu.

- Các Router sẽ chia sẻ trạng thái và các thông tin định tuyến cho nhau để chúng có thể quản lý lưu lượng và tránh được các kết nối chậm.

### 1.4 Phân loại định tuyến

![hinh_1.4](/LinhNH/06.Timhieu_Routing/images/phanloai.png)

__Routing được chia làm 2 phương thức chính là Static Routing và Dynamic Routing.__

- Static Routing (Định tuyến tĩnh)

Trong định tuyến tĩnh, quản trị viên mạng sử dụng bảng tĩnh để đặt cấu hình và chọn các tuyến mạng theo cách thủ công. Định tuyến tĩnh hữu ích trong các tình huống mà thiết kế mạng hoặc các thông số dự kiến sẽ không thay đổi.

Bản chất tĩnh của kỹ thuật định tuyến này đi kèm với những hạn chế dự kiến, chẳng hạn như tắc nghẽn mạng. Mặc dù quản trị viên có thể đặt cấu hình đường dẫn dự phòng trong trường hợp một liên kết bị lỗi, định tuyến tĩnh thường làm giảm khả năng thích ứng và linh hoạt của mạng, dẫn đến hiệu suất mạng bị hạn chế.

- Dynamic Routing (Định tuyến động)

Trong định tuyến động, các bộ định tuyến tạo và cập nhật bảng định tuyến trong thời gian chạy dựa trên điều kiện mạng thực tế. Bộ định tuyến cố gắng tìm đường dẫn nhanh nhất từ nguồn đến điểm đích bằng cách sử dụng một giao thức định tuyến động, đây là một tập hợp các quy tắc giúp tạo, duy trì và cập nhật bảng định tuyến động.

Lợi thế lớn nhất của định tuyến động là khả năng thích ứng với các điều kiện mạng thay đổi, bao gồm lưu lượng truy cập, băng thông và lỗi mạng.

### 1.5 Thuật toán định tuyến
## 2. Tìm hiểu về Static Routing

_Static routing là phương thức định tuyến mà người quản trị sẽ nhập tất cả thông tin về đường đi cho router. Khi cấu trúc hệ thống mạng có bất kỳ sự thay đổi nào thì người quản trị sẽ thay đổi bằng cách xóa hay thêm các thông tin về đường đi cho router, nói cách khác đường đi này là cố định._

__Nguyên lý hoạt động:__

- Đầu tiên người quản trị sẽ cấu hình các đường cố định cho router
- Router sẽ cài đặt đường đi này vào bảng định tuyến
- Gói dữ liệu được định tuyến theo đường cố định.

__Ưu điểm:__

- Cấu hình dễ dàng và nhanh chóng
- Hỗ trợ ở tất cả các thiết bị định tuyến và router
- Sử dụng ít băng thông hơn so với các phương thức định tuyến khác.

__Nhược điểm:__

- Độ phức tạp của cấu hình sẽ tăng khi kích thước hệ thống mạng tăng
- Không thích hợp với hệ thống mạng lớn vì không thể thích ứng được với sự thay đổi của hệ thống mạng
- Khả năng cập nhật đường đi bị hạn chế bởi vậy nguy cơ tràn băng thông là rất cao.

__Cách cấu hình cơ bản:__

Static routing thường được sử dụng khi cần định tuyến từ một Netwwork đến một Stub Network, (stub Network là một mạng con chỉ có một tuyến đường duy nhất để đi ra bên ngoài).

Static routing cũng được dùng để xác định một phương án cuối cùng để gửi một gói tin không rõ địa chỉ đích.

__Cú pháp lệnh Static routing:__

    R(config)# ip route network [mask] {Address|interface}[distance]  [parmanent]



