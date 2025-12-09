1. File cấu hình cần sửa
Trên Ubuntu, file server block mặc định nằm ở:
`/etc/nginx/sites-available/default`
Đây là file quan trọng nhất để đổi port.
Mở file:

       sudo nano /etc/nginx/sites-available/default

2. Tìm và sửa dòng listen 80

Trong file bạn sẽ thấy:


    server {
        listen 80 default_server;
        listen [::]:80 default_server;

        root /var/www/html;

→ Đổi cả 2 dòng thành port bạn muốn, ví dụ 8080:

    server {
        listen 8080 default_server;
        listen [::]:8080 default_server;

        root /var/www/html;

3. Mở firewall (nếu dùng UFW)


Nếu bật UFW:

    sudo ufw allow 8080/tcp

4. Kiểm tra cấu hình

        sudo nginx -t

Nếu OK:
syntax is ok
test is successful

5. Restart Nginx

       sudo systemctl restart nginx

 6. Truy cập thử

        http://IP:8080

![alt text](image-25.png)