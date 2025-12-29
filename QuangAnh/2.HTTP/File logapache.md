# 1.Bắt đầu với ghi nhật ký Apache(Log apache)
Nhật ký Apache (Log apache) là các tệp ghi lại mọi hoạt động của máy chủ web Apache để quản trị viên máy chủ phân tích sau này. Bản ghi của tất cả các sự kiện Apache được lưu trong hai tệp văn bản khác nhau:

 **Nhật ký Truy cập** : Nhật ký truy cập ghi lại tất cả các yêu cầu được gửi đến máy chủ. Chúng thường bao gồm các thông tin như địa chỉ IP của máy khách, thời gian yêu cầu, URL được yêu cầu, mã trạng thái HTTP và tác nhân người dùng.

Ví dụ:

    127.0.0.1 - frank [18/Jul/2024:13:55:36 -0700] "GET /apache_pb.gif HTTP/1.0" 200 2326

Giải thích về các thành phần:

- `127.0.0.1`: Địa chỉ IP của máy khách đưa ra yêu cầu.
- `frank`: Mã định danh người dùng cho máy khách, thường được cung cấp bởi xác thực HTTP.
- `[18/07/2024:13:55:36 -0700]`: Ngày và giờ thực hiện yêu cầu, theo sau là độ lệch múi giờ.

- `"GET /apache_pb.gif HTTP/1.0"`: Dòng yêu cầu từ máy khách. Bao gồm:
  - `GET:` Phương thức HTTP được sử. dụng.
  - `/apache_pb.gif`: URL được yêu. cầu.
  - `HTTP/1.0`: Phiên bản giao thức. HTTP được sử dụng.
- `200`: Mã trạng thái HTTP được máy chủ trả về, cho biết kết quả của yêu cầu (200 nghĩa là OK).
- `2326`: Kích thước của phản hồi tính bằng byte, không bao gồm tiêu đề.


 **Nhật ký lỗi** : Nhật ký lỗi ghi lại các sự cố mà máy chủ gặp phải trong quá trình xử lý yêu cầu, bao gồm các lỗi như không tìm thấy tệp, cấu hình máy chủ sai, v.v.

Ví dụ:

    [Fri Jul 14 14:32:14.873076 2024] [core:notice] [pid 1234] AH00094: Command line: '/usr/sbin/httpd -D FOREGROUND'

Giải thích về các thành phần:

- `[Fri Jul 14 14:32:14.873076]`: Ngày và giờ xảy ra lỗi, chính xác đến từng micro giây.
- `[core]`: Mô-đun và mức độ nghiêm trọng của thông báo.
  - `core`: Mô-đun nơi phát sinh lỗi hoặc thông báo.
  - `notice`: Mức độ nghiêm trọng của tin nhắn, cho biết tầm quan trọng của nó.
- `[pid 1234]`: ID tiến trình của tiến trình máy chủ gặp phải sự cố.
- `AH00094`: Mã định danh duy nhất cho lỗi hoặc thông báo cụ thể.
- Dòng lệnh: `'/usr/sbin/httpd -D FOREGROUND'`: Dòng lệnh được sử dụng để khởi động máy chủ.

Quản trị viên máy chủ, nhà phát triển và nhà phân tích sử dụng các nhật ký này để chẩn đoán sự cố, giám sát bảo mật và phân tích các mẫu lưu lượng truy cập trên máy chủ web

# 2.Xác định vị trí các tệp nhật ký Apache

Vị trí của tệp nhật ký phụ thuộc vào hệ điều hành mà máy chủ web Apache đang chạy. Trên các hệ điều hành dựa trên Debian như Ubuntu, tệp nhật ký truy cập nằm ở thư mục `/var/log/apache2/access.log` . 


Trên CentOS, RHEL hoặc Fedora, tệp nhật ký truy cập được lưu trữ ở thư mục `/var/log/httpd/access_log`.

Tương tự, tệp nhật ký lỗi nằm trong `/var/log/apache2/error.log`các hệ thống dựa trên Debian và `/var/log/httpd/error_log`trên CentOS, RHEL hoặc Fedora
#  3 . Xem tệp nhật ký Apache

- `Tail . Lệnh tail` hiển thị một số mục nhập cuối cùng trong tệp nhật ký. Thêm -ftùy chọn để bật cập nhật theo thời gian thực trong cửa sổ terminal. Ví dụ:
   
      sudo tail -f /var/log/apache2/access.log

Bạn sẽ thấy kết quả sau trên màn hình:

Để xem toàn bộ nội dung của tệp, bạn có thể sử dụng `cat`lệnh hoặc mở tệp trong trình soạn thảo văn bản như `nano`hoặc `vim`:

    cat /var/log/apache2/access.log

- `Grep . Lệnh grep` để lọc các mục nhật ký trong tệp nhật ký theo một thuật ngữ cụ thể.  Đối số đầu tiên `grep` là thuật ngữ bạn muốn tìm kiếm, trong khi đối số thứ hai là tệp nhật ký sẽ được tìm kiếm. Trong ví dụ dưới đây, chúng tôi đang lọc tất cả các dòng có chứa từ `GET`:

    sudo grep GET /var/log/apache2/access.log

Điều này sẽ hiển thị kết quả đầu ra sau:





- `Less . Lệnh less` là một trình phân trang đầu cuối giúp đơn giản hóa việc xem các tệp lớn. Các tùy chọn bổ sung cho phép điều hướng tệp và tìm kiếm một từ hoặc mẫu cụ thể trong nội dung tệp. Ví dụ: để xem nhật ký truy cập Apache bằng lệnh này, hãy chạy:

      less /var/log/apache2/access.log

# 4.Kiểm tra định dạng nhật ký truy cập Apache

Nhật ký truy cập ghi lại tất cả các yêu cầu được máy chủ xử lý. Bạn có thể xem những tài nguyên nào đang được yêu cầu, trạng thái của từng yêu cầu và thời gian xử lý phản hồi.

` Common Log Format` này kiểm soát vị trí và định dạng của tệp nhật ký truy cập Apache. Chỉ thị này có thể được đặt trong tệp cấu hình máy chủ `( /etc/apache2/apache2.conf)` hoặc trong mục nhập máy chủ ảo của bạn. Lưu ý rằng việc định nghĩa cùng một `Common Log Format` trong cả hai tệp có thể gây ra sự cố.

## 4.1 Common Log Format
`Common Log Format (CLF) ` là một định dạng chuẩn để ghi lại các thông tin trong file log truy cập của máy chủ web như Apache. Nó giúp thống nhất cách ghi nhận dữ liệu truy cập từ các client để dễ dàng phân tích và xử lý.. Định dạng này được định nghĩa trong `/etc/apache2/apache2.conf`tệp cấu hình thông qua LogFormat.

Khi bạn chạy lệnh dưới đây:

    sudo grep common /etc/apache2/apache2.conf

![alt text](/QuangAnh/HTTP/image/image-32.png)

Dòng trên định nghĩa biệt danh `common`và liên kết nó với một chuỗi định dạng nhật ký cụ thể. Một mục nhật ký được tạo theo định dạng này sẽ trông như thế này:

    127.0.0.1 alice Alice [06/June/2025:11:26:42 +0200] "GET / HTTP/1.1" 200 3477

Sau đây là lời giải thích về thông tin có trong thông báo nhật ký ở trên:

- `%h`→ `127.0.0.1`: tên máy chủ hoặc địa chỉ IP của máy khách đã đưa ra yêu cầu.
- `%l`→ `alice`: tên nhật ký từ xa (tên dùng để đăng nhập người dùng). Giá trị giữ chỗ (` -`) sẽ được sử dụng nếu giá trị này không được đặt.
- `%u`→ `Alice`: tên người dùng từ xa (tên người dùng của người dùng đã đăng nhập). Giá trị giữ chỗ ( `-`) sẽ được sử dụng nếu giá trị này không được đặt.
- `%t`→ `[06/June/2025:11:26:42 +0200]`: ngày và giờ yêu cầu.
- `\"%r\"`→ `"GET / HTTP/1.1"`- phương thức yêu cầu, tuyến đường và giao thức.
- `%>s`→ `200`- mã phản hồi.
- `%O`→ `3477`- kích thước của phản hồi tính bằng byte.

## 4.2 Combined Log Format

Combined Log Format  rất giống với định dạng Common Log Format nhưng chứa ít thông tin bổ sung hơn.

Nó cũng được định nghĩa trong `/etc/apache2/apache2.conf`tệp cấu hình:

 

    sudo grep -w combined /etc/apache2/apache2.conf

Bạn sẽ thấy kết quả sau:

![alt text](/QuangAnh/HTTP/image/image-33.png)

Lưu ý rằng định dạng này hoàn toàn giống với Common Log Format, chỉ khác là có thêm hai trường. Các mục nhập được tạo theo định dạng này sẽ trông như thế này:

    127.0.0.1 alice Alice [06/June/2025:11:18:36 +0200] "GET / HTTP/1.1" 200 3477 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.93 Safari/537.36"

Sau đây là lời giải thích về hai trường bổ sung không có trong định dạng Nhật ký chung:

- `\"%{Referer}i\"`→ `"-"`: URL của người giới thiệu (nếu có, nếu không -thì sử dụng).
- `\"%{User-Agent}i\"`-> `"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/90.0.4430.93 Safari/537.36"`: thông tin chi tiết về tác nhân người dùng của máy khách đã thực hiện yêu cầu.