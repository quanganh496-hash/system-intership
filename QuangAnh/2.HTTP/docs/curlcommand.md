# Lệnh curl
 Curl là một trong những dự án mã nguồn mở lâu đời và phổ biến nhất trên thế giới. cURL là từ viết tắt của **Client URL** - một công cụ dòng lệnh (command line tool) được sử dụng để kiểm tra kết nối từ URL, thực hiện truyền dữ liệu giữa các máy chủ và thiết bị. Với giao thức HTTP, cURL hỗ trợ việc gửi đi một request với tất cả các phương thức hiện có như GET, POST, PUT, DELETE…

![alt text](/QuangAnh/HTTP/image/image-21.png)

## 2. Lịch sử hình thành và phát triển của cURL

Dưới đây là một cái nhìn tổng quan về lịch sử hình thành và phát triển của cURL:

- Bắt đầu với libcurl: cURL bắt đầu dưới dạng một thư viện gọi là libcurl, được phát triển bởi Daniel Stenberg từ năm 1997. Ban đầu, nó được thiết kế để hỗ trợ truy cập vào các tài nguyên từ các máy chủ web bằng dòng lệnh Unix.
- Ra đời của cURL Command Line Tool: Sau khi libcurl trở nên phổ biến, Daniel Stenberg đã phát triển một công cụ dòng lệnh riêng biệt được gọi là cURL. Công cụ này cung cấp một giao diện dễ sử dụng để truy cập và tương tác với các tài nguyên web từ dòng lệnh.
- Open Source và Độ phổ biến: cURL Linux nhanh chóng trở thành một trong những công cụ phổ biến nhất cho việc truy cập web từ dòng lệnh. Sự phổ biến của nó phần lớn là nhờ tính năng đa dạng, dễ sử dụng và mã nguồn mở, cho phép những người sử dụng và nhà phát triển trên toàn thế giới tùy chỉnh và tích hợp nó vào các dự án của họ.
- Hỗ trợ cho nhiều giao thức: cURL Linux không chỉ hỗ trợ các giao thức phổ biến như HTTP và FTP mà còn hỗ trợ SCP, SFTP, LDAP, và nhiều giao thức khác nữa.
- Sự phát triển liên tục: Cộng đồng mã nguồn mở đã tiếp tục phát triển và cải tiến cURL Linux qua các phiên bản mới, đảm bảo tính năng mới và bảo mật. Các bản cập nhật thường xuyên được phát hành để sửa lỗi và cải thiện hiệu suất.
- Tích hợp và Sử dụng rộng rãi: cURL Linux không chỉ được sử dụng từ dòng lệnh mà còn được tích hợp vào nhiều ứng dụng, frameworks và ngôn ngữ lập trình khác nhau như PHP, Python, Ruby, và nhiều ngôn ngữ khác.

## 3. Các giao thức cURL Command hỗ trợ

cURL Linux tương thích với đa dạng giao thức. Tuy nhiên, nếu không chỉ định giao thức nào, cURL tự động chọn HTTP làm giao thức mặc định. Dưới đây liệt kê các giao thức mà cURL Linux có khả năng hỗ trợ:

![alt text](/QuangAnh/HTTP/image/image-20.png)

Lưu ý rằng danh sách cụ thể các giao thức được hỗ trợ có thể thay đổi tùy thuộc vào phiên bản cURL và cách nó được biên dịch. Để kiểm tra các giao thức được hỗ trợ trong phiên bản cURL Linux cụ thể của bạn, bạn có thể chạy lệnh curl –version trong terminal hoặc command prompt.

## Chức năng của cURL

1. Gửi và nhận dữ liệu qua Internet

- curl có thể gửi yêu cầu (request) đến một máy chủ web và nhận phản hồi (response).

- Hỗ trợ nhiều giao thức mạng như:
HTTP, HTTPS, FTP, SFTP, SMTP, IMAP, POP3, v.v.

📌 Ví dụ:

     curl https://example.com


→ Lấy mã HTML của trang web.

 2. Gọi API (làm việc với web service)

- curl thường dùng để gửi dữ liệu JSON hoặc form đến máy chủ API.

📌 Ví dụ:

    curl -X POST -H "Content-Type: application/json" \
         -d '{"username":"quang","password":"123"}' \
        https://api.example.com/login


→ Gửi yêu cầu POST chứa dữ liệu JSON.

3. Tải hoặc tải lên tệp tin

- Dùng curl để tải file từ internet hoặc upload file lên server.

📌 Ví dụ tải file:

    curl -O https://example.com/file.zip


📌 Ví dụ upload file:

    curl -T myfile.txt ftp://ftp.example.com/

4. Kiểm tra thông tin trang web hoặc kết nối

- Xem header, trạng thái HTTP, thời gian phản hồi, v.v.

📌 Ví dụ:

    curl -I https://example.com


→ Hiển thị phần header (thông tin phản hồi của server).

5. Tự động hóa và kiểm thử

- `curl` rất phổ biến trong:

  - Kiểm tra API backend.

  - Viết script tự động (bash, Python, PowerShell).

  - Kiểm tra SSL, token, cookie, redirect, v.v.

## Cú pháp

    curl [options] [URL...]

## Cài. đặt

Mặc dù gói này được cài đặt sẵn trên hầu hết các bản phân phối Linux, bạn có thể dễ dàng tải xuống curl nếu nó chưa được cài đặt trên máy của bạn bằng cách sử dụng các lệnh sau. 

Trên Ubuntu và Debian:

    sudo apt install curl

Trên các bản phân phối dựa trên RHEL như CentOS và Fedora:

    sudo yum install curl

Để cài đặt curl trên Arch Linux, hãy nhập:

    sudo pacman -S curl

## Ví dụ và các option 

1. Hiển thị nội dung của URL trên màn hình

    curl <URL>

![alt text](/QuangAnh/HTTP/image/image-22.png)

Có thể tải nhiều nhiều trang tương tự nhau:

     curl http://site.{one, two, three}.com

Giải thích:

- `{one,two,three}` là tập hợp (set) các giá trị mà `curl` sẽ thay thế lần lượt.

- Lệnh trên tương đương với:

      curl http://site.one.com
      curl http://site.two.com
      curl http://site.three.com


Kết quả là curl sẽ lần lượt hiển thị nội dung của cả 3 trang lên màn hình.

Các trang với chuỗi số:

     curl ftp://ftp.example.com/file[1-20].jpeg

Giải thích:

- [1-20] có nghĩa là curl sẽ lần lượt thay số từ 1 đến 20.

- Nó tương đương với:

      curl ftp://ftp.example.com/file1.jpeg
      curl ftp://ftp.example.com/file2.jpeg
      ...
      curl ftp://ftp.example.com/file20.jpeg


🔸 Bạn cũng có thể dùng ký tự:

      curl ftp://ftp.example.com/file[a-z].txt


→ tải các file filea.txt đến filez.txt.

2. Đồng hồ đo tiến độ (Process Meter)

Nếu bạn muốn theo dõi quá trình tải file như tốc độ truyền, lượng dữ liệu được truyền, thời gian còn lại, ... Ta thêm option -#

Ví dụ:

    curl -# -o hello.zip ftp://speedtest.tele2.net/1MB.zip

![alt text](/QuangAnh/HTTP/image/image-24.png)

3. Lưu file tải về với tên tùy chọn

`curl -o [file_name] [url]`

     curl -O http://speedtest.tele2.net/1MB.zip


![alt text](/QuangAnh/HTTP/image/image-23.png)

| Cột                   | Ý nghĩa                   |
| --------------------- | ------------------------- |
| `% Total`             | % tổng dung lượng cần tải |
| `% Received`          | % đã tải xong             |
| `% Xferd`             | % dữ liệu đã truyền       |
| `Average Speed Dload` | Tốc độ tải trung bình     |
| `Time Total`          | Thời gian ước tính tổng   |
| `Time Spent`          | Thời gian đã trôi qua     |
| `Time Left`           | Thời gian còn lại         |
| `Current Speed`       | Tốc độ tải hiện tại       |


4. Tải file với tên giống trên URL

`curl -O [url]`

     curl -O http://speedtest.tele2.net/1MB.zip

![alt text](/QuangAnh/HTTP/image/image-25.png)

Tải xuống nhiều tệp:

     curl -O [url_1] -O [url_2] ...

5. Tiếp tục tải xuống các file bị gián đoạn

`curl -C - [url]`

     curl -C - -O ftp://speedtest.tele2.net/1MB.zip

6. Tải file có yêu cầu xác thực từ FTP Server

`# curl -u {username}:{password} [FTP_URL]` Ví dụ: Tải file có xác thực theo cách thông thường sẽ bị lỗi

     curl -O http://test.rebex.net/readme.txt

![alt text](/QuangAnh/HTTP/image/image-26.png)

7. Truy vấn HTTP Header

`curl -I [URL]` Ví dụ:

![alt text](/QuangAnh/HTTP/image/image-27.png)

8. Lưu trữ 1 cookie

       curl -c [tên_file_cookie] [url] -O

- -c = --cookie

Ví dụ

     curl --cookie-jar cnncookies.txt https://www.cnn.com/index.html -O

10. Giới hạn download

         curl --limit-rate [value] [URL]

Tốc độ download sẽ được giữ xung quanh giới hạn ta đặt.

value : đơn vị là bytes.

Ví dụ:

      curl --limit-rate 1000K -O ftp://speedtest.tele2.net/1MB.zip

![alt text](/QuangAnh/HTTP/image/image-28.png)

11. Mô phỏng các Method HTTP

Cú pháp:

    curl -X [Method] [URL] -H "<Content_Type_Header>" -d "<data>"
Trong đó:

- -X [Method]: Khai báo method sử dụng GET, POST, DELETE, PUT
- -H "<Content_Type_Header>": Header với kiểu nội dung của nó
- -H "Content-Type: application/x-www-form-urlencoded" : Data dạng không mã hóa
- -H "Content-Type: application/json": Data dạng Json
[URL] : url trang web
- -d "" : dữ liệu kèm Method. Có thể dùng string hoặc file.
- Dạng không mã hóa: -d "param1=value1&param2=value2" hoặc -d @data.txt
- Dạng Json: -d '{"key1":"value1", "key2":"value2"}' hoặc -d @data.json

Ví dụ: POST với data là username và password lên 1 trang đăng nhập của 1 web:

POST dạng không mã hóa:
 
    curl -X POST http://localhost:3000/data -d "param1=value1&param2=value2" 
hoặc có Header:

     curl -X POST http://localhost:3000/data -H "Content-Type: application/x-www-form-urlencoded" -d "param1=value1&param2=value2"  
Với file:

    curl -X POST http://localhost:3000/data -d "@data.txt" 
POST dạng Json

     curl -X POST http://localhost:3000/data -H "Content-Type: application/json" -d '{"key1":"value1", "key2":"value2"}' 
Với file:

     curl -X POST http://localhost:3000/data -d "@data.json" 
File. data.txt

     param1=value1&param2=value2
File data.json

     {
       "key1":"value1",
       "key2":"value2"
     }
