# 1. Proxy
Proxy (còn được gọi là Proxy server) là máy chủ trung gian, đóng vai trò như một cổng kết nối giữa người dùng và internet. Proxy có chức năng tương tự như một bức tường lửa (firewall) hay một bộ lọc truy cập trang web, đảm bảo các kết nối được an toàn khi sử dụng.

![alt text](image-13.png)


# 2. Chức năng của máy chủ Proxy

![alt text](image-14.png)

Proxy HTTP thực hiện nhiều vai trò quan trọng trong quá trình giao tiếp giữa client và server. Một số vai trò cơ bản bao gồm:

- Quản lý và kiểm soát số lượng truy cập vào Internet. 
- Tiết kiệm tối đa băng thông được sử dụng. 
- Cải thiện và tối ưu tốc độ truy cập Internet trên các thiết bị.  
- Bảo mật riêng tư quyền truy cập Internet. 
- Tiếp cận, truy cập những nguồn dữ liệu bị chặn. 

# 3. Nguyên lý hoạt động của Proxy Server

Như mọi người đã biết, mọi máy tính trên Internet đều phải có địa chỉ IP duy nhất và địa chỉ IP này là giống như địa chỉ nhà của bạn vậy. Cũng giống như các bưu điện cần biết địa chỉ nhà của bạn để chuyển phát thư, Internet cũng cần biết địa chỉ IP máy tính của người dùng để gửi dữ liệu đến đúng máy tính đó.
Proxy Server về cơ bản là một máy tính trên Internet với địa chỉ IP của riêng nó mà máy tính của bạn biết. Khi gửi một yêu cầu web, nó sẽ đến Proxy Server đầu tiên. Sau đó, Proxy Server sẽ thực hiện yêu cầu web và thu thập phản hồi từ máy chủ web và chuyển tiếp dữ liệu trang web để người dùng nhìn thấy các trang web trong trình duyệt.
Khi Proxy Server chuyển tiếp yêu cầu web của người dùng, nó có thể thay đổi dữ liệu đó mà vẫn lấy thông tin theo đúng yêu cầu. Máy chủ Proxy có thể thay đổi địa chỉ IP để máy chủ web không thể nắm rõ được chính xác vị trí của người dùng, cùng với đó việc mã hóa dữ liệu cũng giúp nâng cao hơn độ bảo mật trong quá trình vận chuyển. Và cuối cùng Proxy Server có thể giúp chặn các truy cập vào các trang web cụ thể dựa trên địa chỉ IP.

![alt text](image-15.png)

# 4. loại Proxy Server phổ biến hiện nay

1. Forward Proxy (Proxy thuận)

 Forward proxy (hay proxy thuận) là máy chủ trung gian đứng giữa client và Internet.
Nó thay mặt người dùng (client) gửi yêu cầu tới web server, nhận phản hồi rồi chuyển ngược lại cho client.

 Người dùng phải biết và cấu hình proxy (ví dụ nhập địa chỉ proxy vào trình duyệt hoặc hệ điều hành)

⸻

 2. Reverse Proxy (Proxy nghịch)

Ngược lại với forward proxy, reverse proxy nằm ở phía máy chủ.
Nó tiếp nhận các yêu cầu HTTP từ Internet, rồi chuyển tiếp đến một hoặc nhiều web server ở phía sau.

 Cách hoạt động:
-  Người dùng gửi yêu cầu đến một địa chỉ (ví dụ: example.com).
- Reverse proxy nhận yêu cầu, rồi phân phối nó đến các server thật phía sau (backend servers).
- Sau khi xử lý, phản hồi được gửi ngược lại qua proxy.


3. Transparent Proxy (Proxy trong suốt)

- Transparent proxy (proxy trong suốt) là một proxy mà client không cần cấu hình gì cả — lưu lượng mạng bị bắt và chuyển qua proxy “một cách trong suốt” (transparent) bởi mạng (router, firewall, gateway chặn lại). Người dùng tưởng đang kết nối trực tiếp nhưng thực tế lưu lượng HTTP/HTTPS đi qua máy chủ trung gian.

- Proxy này không ẩn địa chỉ IP của client (vì vẫn gửi header thật như X-Forwarded-For).


⸻

 4. Anonymous Proxy

Đây là dạng forward proxy có ẩn danh, dùng để che IP thật của client.

 Đặc điểm:
- Proxy xóa hoặc thay đổi các trường HTTP header như X-Forwarded-For.
- Web server không thể thấy địa chỉ IP thật của người dùng.



5. High Anonymity Proxy (Elite Proxy)

Đây là cấp độ cao hơn của `anonymous proxy`.
Máy chủ web không thể nhận ra rằng bạn đang dùng proxy.

 Đặc điểm:
- Không gửi bất kỳ thông tin nào cho thấy lưu lượng đi qua proxy.
-  Giao tiếp giống hệt như client trực tiếp với web server.

⸻

6. Distorting Proxy(Proxy mạo danh)

Một máy Proxy mạo danh thực hiện chức năng giống với máy chủ vô danh nhưng bằng cách gửi sai địa chỉ IP cho máy chủ web, do đó có thể truy cập vào nội dụng bị chặn.


