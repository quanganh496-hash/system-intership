# Tìm hiểu về Routing

## 1.Giới thiệu về Routing

Routing là quá trình xác định đường đi tốt nhất trên một mạng máy tính để gói tin được tới đích theo một số thủ tục nhất định thông qua các nút trung gian là các bộ định tuyến router.

Routing đóng vai trò quan trọng đến tốc độ việc truyền dữ liệu trong mạng. Không có định tuyến mạng đường truyền dẫn dữ liệu sẽ diễn ra hỗn loạn, có thể khiến các đường truyền bị quá tải, truyền dẫn dữ liệu bị chậm.

Định tuyến trực tiếp quyết định hiệu suất mạng bằng việc xác định đường đi tối ưu nhất để truyền dẫn dữ liệu, tránh các đường truyền dẫn quá tải và phân bố lưu lượng mạng một cách cân đối.

Ngoài ra, định tuyến chính là cách cơ sở để tích hợp các mạng lại với nhau. Và gắn kết tất cả các thiết bị trong một mạng để liên kết và giao tiếp với nhau. Hơn nữa, định tuyến còn liên quan đến việc xây dựng các đường dự phòng hay bảo mật cho hệ thống mạng.

Định tuyến được phân chia thành 2 loại cơ bản:

- Static routing: Việc xây dựng bảng định tuyến của router được thực hiện bằng tay bởi người quản trị.
- Dynamic routing: Việc xây dựng và duy trì trạng thái của bảng định tuyến được thực hiện tự động bởi router.

## 2.Static Routing

Static routing là phương thức định tuyến mà người quản trị sẽ nhập tất cả thông tin về đường đi cho router. 
Khi cấu trúc hệ thống mạng có bất kỳ sự thay đổi nào thì người quản trị sẽ thay đổi bằng cách xóa hay thêm các thông tin về đường đi cho router, nói cách khác đường đi này là cố định.

Nguyên lý hoạt động:

- đầu tiên người quản trị sẽ cấu hình các đường cố định cho router
- router sẽ cài đặt đường đi này vào bảng định tuyến
- gói dữ liệu được định tuyến theo đường cố định.

Ưu điểm:

- cấu hình dễ dàng và nhanh chóng
- hỗ trợ ở tất cả các thiết bị định tuyến và router
- sử dụng ít băng thông hơn so với các phương thức định tuyến khác.

Nhược điểm:

- độ phức tạp của cấu hình sẽ tăng khi kích thước hệ thống mạng tăng
- không thích hợp với hệ thống mạng lớn vì không thể thích ứng được với sự thay đổi của hệ thống mạng
- khả năng cập nhật đường đi bị hạn chế bởi vậy nguy cơ tràn băng thông là rất cao.

Cách cấu hình cơ bản:

Static Routes thường được sử dụng khi cần định tuyến từ một Netwwork đến một Stub Network, (stub Network là một mạng con chỉ có một tuyến đường duy nhất để đi ra bên ngoài).

Static routes cũng được dùng để xác định một phương án cuối cùng để gửi một gói tin không rõ địa chỉ đích.

Cú pháp lệnh Static route: 

```  
R(config)# ip route network [mask] {Address|interface}[distance][parmanent] 

```

|Tham số lệnh IP route | Mô tả |
|-------|-------|
|Network| Địa chỉ đích đến|
|Address| Địa chỉ IP của router kế tiếp |
|Interface| Tên interface sử dụng|
|Distance| Xác định khoảng cách tới router gần nhất|
|Permanent| Quy định router không bị thay đổi khi có một interface bị down|
|Mask| Subnet mask|


## 3.Lab 

![image1](/HoangNH/6.TimhieuRouting/image/image.png)

Đánh địa chỉ cho R1,R2:

```

Router>enable
Router#configure terminal
Router(config)#hostname R1
R1(config)#interface FastEthernet 1/0
R1(config-if)#ip address 192.168.1.1 255.255.255.0
R1(config-if)#no shutdown
R1(config-if)#exit
R1(config)#interface FastEthernet 0/0
R1(config-if)#ip address 192.168.2.1 255.255.255.0
R1(config-if)#no shutdown
R1(config-if)#exit
```

```
Router>enable
Router#configure terminal
Router(config)#hostname R2
R2(config)#interface FastEthernet 1/0
R2(config-if)#ip address 192.168.1.2 255.255.255.0
R2(config-if)#no shutdown
R2(config-if)#exit
R2(config)#interface FastEthernet 0/0
R2(config-if)#ip address 192.168.3.2 255.255.255.0
R2(config-if)#no shutdown
R2(config-if)#exit
```

Cấu hình cho PC:

![image1](/HoangNH/6.TimhieuRouting/image/pc1.png)

![image1](/HoangNH/6.TimhieuRouting/image/pc2.png)

Cấu hình Static routing:

```
R1(config)# ip route 192.168.3.0 255.255.255.0 192.168.1.2
```

