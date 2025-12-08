# Web server là gì?
![alt text](image.png)

Webserver (máy chủ web) là một hệ thống phần mềm hoặc phần cứng chuyên lưu trữ và gửi nội dung của trang web (HTML, hình ảnh,…) đến trình duyệt của người dùng khi có yêu cầu. Ví dụ, bạn gõ địa chỉ một trang web trên trình duyệt, máy chủ web sẽ nhận yêu cầu này và trả về dữ liệu trang web để trình duyệt hiển thị

# Các thành phần chính của một Webserver
![alt text](image-2.png)

Hình ảnh trên minh họa một ví dụ về máy chủ vật lý đặt trong trung tâm dữ liệu (datacenter) – nơi chứa phần cứng chuyên dụng để chạy phần mềm Webserver. Web server bao gồm cả phần cứng và phần mềm để hoạt động. Dưới đây là mô tả về cả hai phần:

**Phần cứng của Web Server:**

- **Máy chủ (Server)**: Đây là máy tính chạy dịch vụ web server và được kết nối với mạng để giao tiếp với các máy tính khách. Máy chủ thường được trang bị vi xử lý mạnh, bộ nhớ RAM lớn và ổ cứng dung lượng cao để lưu trữ dữ liệu và xử lý yêu cầu từ nhiều người dùng cùng một lúc.
- **Hệ điều hành(Operating System)**: Web server thường chạy trên các hệ điều hành như Linux (ví dụ: Ubuntu, CentOS), Unix (ví dụ: FreeBSD), Windows Server và nhiều hệ điều hành khác. Hệ điều hành cung cấp các dịch vụ, giao diện và khả năng quản lý cần thiết cho hoạt động của web server.
- **Mạng và kết nối**: Web server cần được kết nối vào mạng để có thể truyền nhận dữ liệu qua giao thức TCP/IP. Nó có thể được kết nối thông qua Ethernet, Wi-Fi hoặc các công nghệ mạng khác.

 **Phần mềm Webserver**: 
 
- **Web Server Software**: Đây là phần mềm chạy trên máy chủ và đảm nhiệm việc xử lý yêu cầu từ máy tính khách và phục vụ các tài nguyên web tương ứng. Các phần mềm web server phổ biến bao gồm Apache HTTP Server, Nginx, Microsoft IIS, và Lighttpd.

- **Hệ thống tập tin**: Nơi lưu trữ nội dung tĩnh của website (các file HTML, CSS, hình ảnh, video, …). Khi máy chủ web nhận yêu cầu, nó sẽ tìm trong hệ thống này để lấy tệp cần thiết.

- **Ngôn ngữ lập trình và Framework**: Đôi khi, web server cần hỗ trợ các ngôn ngữ lập trình và framework để xử lý logic ứng dụng web. Ví dụ, để phục vụ các trang web động, web server cần hỗ trợ ngôn ngữ như PHP, Python, Node.js và framework như Django, Flask, Ruby on Rails.

- **Cơ sở dữ liệu (tùy chọn)**: Nếu website dùng dữ liệu động (ví dụ bài viết, thông tin sản phẩm), webserver sẽ kết nối đến cơ sở dữ liệu (chẳng hạn MySQL, PostgreSQL) để lấy hoặc lưu trữ dữ liệu.

Ngoài ra, hệ thống Webserver có thể có thêm các thành phần như bộ cân bằng tải (load balancer) để phân phối yêu cầu qua nhiều máy chủ nhằm tăng hiệu suất, tường lửa (firewall) để bảo vệ, và bộ nhớ đệm (cache) để lưu trữ tạm thời nội dung hay dùng, giúp truy cập nhanh hơn.

# Webserver hoạt động như thế nào?
![alt text](image-1.png)

Quá trình một webserver phục vụ trang web diễn ra qua các bước chính như sau:

1. Yêu cầu (Request): Khi bạn nhập địa chỉ trang web (URL)https://example.com/index.html
 vào trình duyệt, trình duyệt sẽ gửi một yêu cầu HTTP tới máy chủ web tương ứng.

-  Trình duyệt gửi yêu cầu đến DNS để phân giải tên miền thành địa chỉ IP:

    - DNS (Domain Name System) sẽ chuyển đổi tên miền example.com thành địa chỉ IP (ví dụ: 203.0.113.5).
-  Trình duyệt sử dụng địa chỉ IP để gửi yêu cầu đến Webserver:

   - Trình duyệt thiết lập kết nối với Webserver qua giao thức HTTP (port 80) hoặc HTTPS (port 443).
   - Yêu cầu gửi đi sẽ chứa các thông tin chính như:

         GET /index.html HTTP/1.1
         Host: example.com


2. Xử lý yêu cầu: Máy chủ web nhận yêu cầu, phân tích địa chỉ được yêu cầu để xác định trang hoặc tài nguyên cụ thể :
- Nếu là nội dung tĩnh (HTML, CSS, JS, hình ảnh): Webserver tìm kiếm file và gửi phản hồi.
- Nếu là nội dung động (PHP, Python, Node.js…): Webserver gọi trình thông dịch hoặc chương trình phụ trợ để xử lý.
3. Tìm kiếm tài nguyên: Webserver tìm nội dung tương ứng trong hệ thống tập tin hoặc cơ sở dữ liệu của nó. Nếu có, máy chủ sẵn sàng gửi lại cho trình duyệt.
4. Phản hồi (Response): Máy chủ tạo một phản hồi HTTP chứa dữ liệu đã yêu cầu (như nội dung trang HTML và hình ảnh) và gửi nó trở lại cho trình duyệt.
- Nếu thành công: Trả về mã `200 OK` cùng nội dung trang web.
- Nếu lỗi: Trả về các mã lỗi như `404 Not Found`, `500 Internal Server Error`…
5. Hiển thị trang web: Trình duyệt nhận phản hồi từ máy chủ và hiển thị nội dung trang web cho người dùng. Trình duyệt phân tích HTML, tải thêm tài nguyên (CSS, JS, hình ảnh), và hiển thị trang hoàn chỉnh.

Trong trường hợp máy chủ không tìm thấy tài nguyên yêu cầu, nó sẽ trả về lỗi (thường mã 404 “Not Found”) để báo cho trình duyệt biết trang không tồn tại. Quá trình yêu cầu – phản hồi này tuân theo mô hình Client – Server: máy khách (client, ví dụ trình duyệt web) gửi yêu cầu đến máy chủ (server), máy chủ xử lý và trả về kết quả

# Các loại webserver phổ biến
![alt text](image-3.png)

- Apache HTTP server: Apache là web server được sử dụng rộng rãi nhất thế giới. Apache được phát triển và duy trì bởi một cộng đồng mã nguồn mở dưới sự bảo trợ của Apache Software Foundation. Apache được phát hành với giấy phép Apache License là được sử dụng tự do, miễn phí.
- Nginx: là một web server nhẹ, không chiếm nhiều tài nguyên của hệ thống. Nginx còn là một reserse proxy mã nguồn mở. Nginx khá là ổn định, cấu hình đơn giản và hiệu suất cao.
- Internet Information Services (IIS): IIS do Microsoft phát triển, sản phẩm này được tích hợp cùng với hệ điều hành Windows Server. Trong IIS bao gồm nhiều dịch vụ như: dịch vụ Web Server, dịch vụ FTP Server.
- Apache Tomcat: là một Java Servlet được phát triển bởi Apache Software Foundation. Tomcat thực thi các ứng dụng Java Servlet và JavaServer Pages (JSP). Tomcat cung cấp một máy chủ HTTP cho ngôn ngữ Java thuần túy.
- Lighttpd: là một phần mềm mã nguồn mở, an toàn và linh hoạt, đặc biệt miễn phí và được phân phối theo giấy phép BSD. Lighttpd được viết bởi Jan Kneschke. Lighttpd chiếm ít tài nguyên, memory thấp, CPU nhỏ. Lighttpd được phát triển bằng ngôn ngữ C. chạy trên hệ điều hành Linux, Windows, Mac OS,…