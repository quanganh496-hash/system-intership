# 1. WordPress HA là gì?

WordPress High Availability (HA) là một kiến trúc hệ thống được thiết kế để đảm bảo trang web WordPress luôn hoạt động liên tục 24/7, không bị gián đoạn (downtime) ngay cả khi một máy chủ, phần cứng, phần mềm hoặc thành phần nào đó gặp sự cố, bằng cách sử dụng các máy chủ dự phòng (redundancy), cân bằng tải (load balancing) và chuyển đổi dự phòng tự động (automatic failover). Mục tiêu chính là giảm thiểu tối đa thời gian chết, duy trì hiệu suất và đảm bảo trải nghiệm người dùng không bị ảnh hưởng, thường được đo bằng % uptime (ví dụ: 99.999%). 

- Nói ngắn gọn: WordPress HA = WordPress không “chết web” khi có sự cố.

# 2. Tại sao cần HA cho WordPress?
Cần HA (High Availability) cho WordPress vì WordPress mặc định không được thiết kế để chịu lỗi. Khi triển khai theo mô hình thông thường (1 server), chỉ cần một thành phần hỏng là website ngừng hoạt động hoàn toàn.

1. Website không bị downtime, đảm bảo trải nghiệm người dùng.

WordPress chạy trên nhiều thành phần:
- Web server
- PHP
- Database
- Storage

Chỉ cần 1 thành phần lỗi → web down.

HA giúp:
- Server chết → server khác thay thế ngay
- Không gián đoạn người dùng

2. Đảm bảo tính liên tục cho dịch vụ quan trọng

Với các website:
- Thương mại điện tử
- Tin tức
- Dịch vụ doanh nghiệp
- Cổng thông tin

Downtime gây:
- Mất doanh thu(đối với website thương mại điện tử).
- Mất uy tín
- Ảnh hưởng trải nghiệm người dùng

→ HA là yêu cầu bắt buộc, không phải tùy chọn.


3. Uy tín thương hiệu: Đảm bảo tính chuyên nghiệp và đáng tin cậy cho website và doanh nghiệp. 

# 3. Kiến trúc WordPress HA cơ bản:

Hình minh họa dưới đây trình bày một sơ đồ khối đơn giản cho kiến trúc WordPress HA. Người dùng gửi request tới Load Balancer đầu tiên, rồi lần lượt được chuyển đến các máy chủ web chạy WordPress, và cuối cùng các máy chủ này truy cập cơ sở dữ liệu và lưu trữ chia sẻ ở tầng backend. Kiến trúc phân tầng này tách biệt rõ ràng các chức năng: Load Balancer chịu trách nhiệm phân phối truy cập, các Web Server xử lý mã PHP của WordPress, Shared Storage đồng bộ file `wp-content`, và cụm Database MySQL/MariaDB đảm bảo dữ liệu luôn sẵn sàng.
- **Load Balancer**: Nhận tất cả request từ user và phân phối đồng đều đến nhiều máy chủ web phía sau, giúp tránh quá tải. Load Balancer cũng kiểm tra sức khỏe của các node và ngừng gửi traffic đến server bị lỗi.
- **Web Servers (WordPress)**: Gồm nhiều máy chủ (Apache/Nginx + PHP-FPM) chạy mã WordPress giống hệt nhau. Các máy chủ này có thể mở rộng (scale out) theo chiều ngang phía sau Load Balancer để đáp ứng lưu lượng lớn.Các node web phải dùng chung file hệ thống của WordPress, nên cần kết nối tới hệ thống Shared Storage.
- **Shared Storage**: Hệ thống lưu trữ chung chứa thư mục wp-content (bao gồm themes, plugins, uploads) để tất cả Web Server truy xuất và ghi nhận file giống nhau. Ví dụ: có thể dùng NFS/GlusterFS hoặc dịch vụ lưu trữ đám mây (Amazon EFS/S3) để đồng bộ dữ liệu giữa các node.
- **Database Cluster (MySQL/MariaDB HA)**: Cụm cơ sở dữ liệu tách biệt hoàn toàn so với lớp web. Thường triển khai theo mô hình master–slave hay Galera (đa-master) để đảm bảo tính nhất quán và khả năng chịu lỗi cao.Các Web Server chỉ ghi/đọc dữ liệu từ cụm DB này.
- **Luồng request**: Như mũi tên trên sơ đồ, các yêu cầu từ người dùng đi vào Load Balancer, sau đó được chuyển đến một trong các Web Server. Các Web Server xử lý yêu cầu và tương tác với Database Cluster (truy vấn, ghi dữ liệu) đồng thời lưu/truy xuất file media từ Shared Storage.

                      ┌────────────────────┐
                      │       USER         │
                      │  (Client / Browser)│
                      └─────────┬──────────┘
                                │  HTTP / HTTPS
                                ▼
                      ┌────────────────────┐
                      │   LOAD BALANCER    │
                      │ (Nginx / HAProxy)  │ Rocky9 192.168.20.40 
                      └─────────┬──────────┘      tom2
                                │  Phân phối request
             ┌────────────────────────────────────┐
             ▼                                    ▼
      ┌───────────────┐                     ┌───────────────┐
      │ WP SERVER 1   │ Ubutu 192.168.20.26 │ WP SERVER 2   │ Ubutu 192.168.20.41
      │ Apache/Nginx  │           tom       │ Apache/Nginx  │     tom3
      │ PHP-FPM       │                     │ PHP-FPM       │
      │ WordPress     │                     │ WordPress     │
      └───────┬───────┘                     └───────┬───────┘
              │                                     │
              │  Truy cập file                      │
              └──────────┬───────-──────────┬───────┘
                         ▼                  ▼
                 ┌────────────────────────────────┐
                 │       SHARED STORAGE           │
                 │ (NFS / CephFS / Object Storage)│
                 │  wp-content/uploads, plugins   │  Ubuntu  192.168.20.202 tom4
                 └────────────────────────────────┘
                                │
                                │  Truy vấn dữ liệu
                                ▼
                 ┌────────────────────────────────┐
                 │      DATABASE CLUSTER          │
                 │  MySQL / MariaDB (HA)          │
                 │  Master–Slave / Galera         │
                 └────────────────────────────────┘

# Lab về Wordpress HA


