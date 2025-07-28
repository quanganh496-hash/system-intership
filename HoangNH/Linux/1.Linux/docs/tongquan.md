# Tổng quan về Linux

## 1.Linux là gì?

Linux là một hệ điều hành mã nguồn mở phổ biến, được phát triển bởi một cộng đồng toàn cầu các nhà phát triển và người dùng. Điều đặc biệt về Linux là tính mã nguồn mở cho phép bất kỳ ai cũng có thể xem, sửa đổi và phân phối mã nguồn của hệ điều hành này.

## 2.Cấu trúc thư mục trong Linux

![image1](/HoangNH/Linux/1.Linux/image/tree.jpg)

### 2.1./ - Root : Thư mục gốc

- Mỗi tập tin đơn và thư mục được bắt đầu thư mục gốc.
- Chỉ người dùng root mới có quyền ghi trong thư mục này.
- Lưu ý: /root là thư mục home của root user chứ không phải là /.

### 2.2./bin : Các file thực thi của người dùng

- Chứa các tập tin thực thi.
- Các lệnh thường dùng của Linux mà bạn cần để dùng trong chế độ người dùng đơn được lưu ở đây.
- Các lệnh được sử dụng bởi tất cả người dùng trong hệ thống được lưu ở đây.
- Ví dụ: ls, ping,...

### 2.3./sbin : Các file thực thi của hệ thống

- Chứa các tập tin thực thi.
- Các lệnh được lưu trong thư mục này được dùng cho người quản trị và được dùng để bảo trì hệ thống.
- Ví dụ: iptables, ipconfig,...

### 2.4./etc : Các file cấu hình

- Chứa các tập tin cấu hình cần thiết cho tất cả các chương trình.
- Nó cũng chứa các đoạn mã khởi động và tắt mà được dùng để khởi động/dừng các chương trình đơn lẻ.

### 2.5./dev : Các file thiết bị

- Chứa các tập tin thiết bị.
- Nó chứa các tập tin thiết bị đầu cuối như là USB hay bất kỳ thiết bị nào gắn vào hệ thống.

### 2.6./proc : Thông tin tiến trình

- Chứa thông tin về các tiến trình của hệ thống.
- Các tập tin chứa thông tin về các tiến trình đang chạy. Ví dụ: /proc/{pid} directory >>> lưu thông tin về tiến trình với pid bạn chọn.
- Các tập tin hệ thống ảo với nội dung về tài nguyên hệ thống. Ví dụ: /proc/uptime

### 2.7./var : Các file biến đổi

- Chứa đựng các file có sự thay đổi trong quá trình hoạt động của hệ điều hành cũng như các ứng dụng. 
- Ví dụ: Nhật ký của hệ thống /var/log,  database file /var/lib

### 2.8./tmp: Thư mục chứa các file tạm

- Thư mục chứa các tập tin tạm được tạo bởi hệ thống và người dùng.
- Các tập tin trong thư mục này bị xóa khi hệ thống khởi động lại.

### 2.9./usr : Chứa các file binary, library, tài liệu, source-code cho các chương trình.

- /usr/bin chứa file binary cho các chương trình của user. Nếu như một user trong quá trình thực thi một lệnh ban đầu sẽ tìm kiếm trong /bin, nếu như không có thì sẽ tiếp tục nhìn vào /usr/bin. Ví dụ một số lệnh như at. awk, cc...
- /usr/sbin chứa các file binary cho system administrator. Nếu như ta không tìm thấy các file system binary bên dưới /sbin thì ta có thể tìm ở trong /usr/sbin. Ví dụ một số lệnh như cron, sshd, useradd, userdel
- /usr/lib chứa các file libraries cho /usr/bin và /usr/sbin
- /usr/local dùng để chứa chương trình của các user, các chương trình này được cài đặt từ source. Ví dụ khi ta install apache từ source thì nó sẽ nằm ở vị trí là /usr/local/apache2


### 2.10./home : Thư mục người dùng

- Chứa các tập tin của các người dùng trong hệ thống.
- Ví dụ: /home/john 

### 2.11./boot : Các file khởi động

- Chứa những tập tin liên quan tới chương trình quản lý khởi động máy.
- Các tập tin initrd, vmlinux, grub được lưu trong thư mục /boot

### 2.12./lib : Thư viện hệ thống

- Chứa các tập tin thư viện để hỗ trợ các file được lưu trong /bin và /sbin
- Tên của các tập tin này là ld* hay lib*.so.*
- Ví dụ: ld-2.11.1.so, libncurses.so.5.7

### 2.13./opt : Các ứng dụng tùy chọn

- Chứa các ứng dụng thêm của các nhà cung cấp khác nhau.
- Các ứng dụng này nên được cài trong thư mục con của thư mục /opt/.

### 2.14./mnt : 

- Thư mục mount tạm thời nơi mà người quản trị hệ thống có thể mount các tập tin hệ thống.
- Mount là một quá trình mà trong đó hệ điều hành làm cho các tập tin và thư mục trên một thiết bị lưu trữ có thể truy cập được bởi người dùng thông qua hệ thống tệp của máy tính.

### 2.15./media :

- Thư mục chưa các mount tạm thời cho các thiết bị tháo lắp.
- Ví dụ: /medica/cdrom cho CD-ROM; /media/floppy cho ổ đĩa mềm; /media/cdrecorder cho ổ đĩa ghi CD.

### 2.16./srv : Dữ liệu dịch vụ

- Chứa dữ liệu liên quan tới các dịch vụ trên máy chủ.
- Ví dụ: /srv/cvs chứa dữ liệu liên quan tới CVS.

## 3.Ưu điểm, hạn chế của Linux

### 3.1.Ưu điểm:

- Bản quyền miễn phí: Linux là một mã nguồn mở và người dùng có thể xem được gần như tất cả code của hệ điều hành này.
- Phù hợp với lập trình viên và quản trị mạng: Linux có một mức độ ổn định và hiệu năng đáng kinh ngạc. Vì vậy nó có thể được sử dụng để làm việc với những lĩnh vực yêu cầu độ ổn định của hệ thống như công việc của lập trình viên hoặc quản trị mạng.
- Hỗ trợ kỹ thuật nhanh: Linux có bộ phận hỗ trợ kỹ thuật phục vụ bất kỳ thời gian nào trong ngày.
- Tính linh hoạt cao: Linux có khả năng tương thích được nhiều môi trường nên các lập trình viên rất thích sử dụng để phát triển các dự án của mình.
- Bảo mật tốt: Khi có virus xuất hiện, chỉ cần xóa là có thể ngăn chặn được.
- Chạy ổn định cả trên các máy tính cấu hình yếu.

### 3.2.Hạn chế:

- Số lượng ứng dụng hỗ trợ vẫn còn rất hạn chế.
- Một số nhà sản xuất không phát triển driver hỗ trợ nền tảng Linux.
- Mất thời gian để làm quen, đặc biệt là khi chuyển từ Windows sang sử dụng Linux thì sẽ cần thời gian để thích nghi từ đầu.

## 4.Linux command

Linux command là một chương trình hoặc tiện ích chạy trên dòng lệnh. Dòng lệnh là giao diện chấp nhận các dòng văn bản và xử lý chúng thành hướng dẫn cho máy tính của bạn.

Một số Linux command phổ biến:

- pwd: In đường dẫn của thư mục làm việc hiện tại.
- cd: Thay đổi thư mục làm việc.
- ls: Liệt kê nội dung của thư mục.
- cat: In nội dung của tệp.
- cp: Sao chép tệp và thư mục.
- mv: Di chuyển hoặc đổi tên tệp và thư mục.
- rm: Xóa tệp và thư mục.
- mkdir: Tạo thư mục.
- rmdir: Xóa thư mục.
- touch: Tạo tệp trống.
- sudo: Cho phép người dùng thực thi các lệnh với quyền root.

## 5.Các loại user trong Linux

Khi một máy tính đuợc sử dụng bởi nhiều người, trong cùng một thời điểm, việc chia riêng biệt những người dùng đó ra là một điều cần thiết. Điều này quan trọng ngay cả khi chỉ có duy nhất một người sử dụng máy tại một thời điểm. Do đó , mỗi người dùng sẽ có một username độc nhất, và username đó đuợc sử dụng để đăng nhập.

Một người dùng có nhiều cái để nhắc đến hơn là username của họ. Một người dùng là tất cả các files, các tài nguyên, và các thông tin thuộc về một người dùng. Bạn có thể liên tưởng tới một ngân hàng, mỗi một tài khoản trong ngân hàng sẽ có một lượng tiền đi kèm ,cùng một vài thông tin phụ thêm khác.

### 5.1.Super user

Root - hay còn gọi là Super user là người có quyền hạn cao nhất trong Linux. Root có tất cả các quyền truy cập vào hệ thống. Bạn có thể cấp quyền cho một người dùng với đầy đủ quyền như một Root, nhưng bạn phải cực kì cẩn trọng và hiểu rõ việc bạn làm.

### 5.2.Regular user

Tài khoản để hoàn thiện những công việc thường ngày như soạn thảo văn bản, duyệt web.... Họ bị giới hạn trong quyền truy cập vào hệ thống và phải dùng quyền của sudoer để thực hiện những tác vụ quản trị.


## 6.Distro Linux

Distro là từ viết tắt thay thế cho Linux Distribution - bản phân phối của Linux - là một hệ điều hành được tập hợp từ nhiều phần mềm dựa trên nhân Linux (Linux Kernel) và thường có một hệ thống quản lý các gói tin.

Thành phần: Một bản distro điển hình bao gồm: một kernel Linux, các công cụ và thư viện GNU, các phần mềm thêm vào, phần document, một hệ thống window system (mà phần lớn là sử dụng X Window System - hệ thống cửa sổ dùng để hiển thị đồ họa Bitmap), window manager và desktop environment.

Hiện tại, có khoảng 600 bản distro tồn tại, với gần 500 trong số đó phát triển tích cực, liên tục được sửa đổi và cải thiện. Bởi sự sẵn có của số lượng lớn phần mềm, distro khá là đa dạng về hình thức - phù hợp với từ desktop, server, laptop, netbooks, điện thoại di động, máy tính bảng cũng như môi trường tối thiếu thường để sử dụng trong các hệ thống nhúng.

Có nhiều bản phân phối thương mại như Fedora (Red hat), OpenSUSE (SUSE), Ubuntu (Canonical Ltd); và hoàn toàn phân phối dựa vào cộng đồng như Debian, Slackware, Gentoo hay Arch Linux.

Các nhánh distro phổ biến:

Debian:

![image2](/HoangNH/Linux/1.Linux/image/debian.png)

- Là một bản phân phối phi thương mại và là một trong những bản phân phối ra đời sớm nhất, duy trì bởi một cộng đồng phát triển tình nguyện với một cam kết mạnh mẽ cho nguyên tắc phần mềm miễn phí và quản lý dự án dân chủ.
- Có 3 dạng khác nhau:

  - Phiên bản ổn định mà người dùng được khuyến khích sử dụng.
  - Phiên bản không ổn định.
  - Phiên bản thử nghiệm cho những ai mong muốn có được phần mềm mới nhất.

- Hệ thống gói quản lý phần mềm sử dụng:

  - dpkg  cài đặt các gói phần mềm .deb
  - apt cài đặt phần mềm từ các kho trên mạng.

- Có khá nhiều distro phát triển dựa trên distro Debian như: Raspbian, Knoppix, Astra Linux, Kali Linux, ... và phổ biến nhất là nhánh Ubuntu.

Fedora:

![image3](/HoangNH/Linux/1.Linux/image/fedora.jpg)

- Là một bản phân phối cộng đồng được "đỡ đầu" bởi một công ty của Mỹ - Red Hat. Nó được tạo ra nhằm kiểm thử các công nghệ cho một bản phân phối thương mại khác của Red Hat - nơi mà các phần mềm nguồn mở mới được tạo lập, phát triển và kiểm thử trong môi trường cộng đồng trước khi được đưa vào Red Hat Enterprise Linux.
- Chu kì ra phiên bản mới của Fedora là 6 tháng. Phiên bản mới với các tính năng bảo mật mà các chuyên gia đánh giá khá tốt.
- Có thể nâng cấp lên phiên bản mới mà không cần cài đặt lại.
- Dùng yum để quản lý các gói phần mềm định dạng .rpm
- Fedora có thể dùng cho máy tính để bàn và máy trạm, thậm chí máy chủ; dành cho những người mới tiếp cận PMTDNM hay những người đã có nhiều kinh nghiệm.
- 2 distro phổ biến nhất được phát triển dựa trên Fedora là Red Hat Enterprise Linux - với đối tượng hướng tới là các doanh nghiệp và công ty lớn (tất nhiên là có tính phí) ; và CentOS - free và hướng tới đối tượng là người sử dụng cá nhân.




