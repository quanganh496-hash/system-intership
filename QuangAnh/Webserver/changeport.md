# Rocky9

1. Mở file cấu hình Apache

       sudo vi /etc/httpd/conf/httpd.conf

Tìm dòng:

    Listen 80

➡ Đổi 80 thành port bạn muốn, ví dụ 8080:

    Listen 8080

 2. (Tùy chọn) Đổi VirtualHost

Nếu bạn đang dùng VirtualHost:

Mở file vhost:

    sudo vi /etc/httpd/conf.d/vhost.conf


Đổi:
`<VirtualHost *:80>`
 thành:
`<VirtualHost *:8080>`


3. Khởi động lại Apache

       sudo systemctl restart httpd

4. Kiểm tra Apache đang nghe port nào

       sudo ss -tulpn | grep httpd

![alt text](image-11.png)

 Truy cập thử
Ví dụ đổi sang 8080:
Truy cập:

     http://IP_cua_ban:8080

![alt text](image-12.png)

# Ubuntu

1. Mở file cấu hình Apache ports.conf

       sudo nano /etc/apache2/ports.conf

Tìm dòng:

Listen 80

Đổi sang port bạn muốn, ví dụ 8080:

Listen 8080

2. Sửa Virtual Host (nếu có)
Mở file cấu hình site (thường là 000-default.conf):

       sudo nano /etc/apache2/sites-available/000-default.conf
 
Sửa:
`<VirtualHost *:80>`
thành:
`<VirtualHost *:8080>`

 3. Kiểm tra xem port có bị chặn firewall không

Nếu dùng UFW:

     sudo ufw allow 8080

4. Restart Apache

       sudo systemctl restart apache2

 5. Truy cập thử

Mở trình duyệt:

     http://your-ip:8080

![alt text](image-13.png)

