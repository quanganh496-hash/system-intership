# Triển khai website wordpress với stack LAMP, LEMP

## Mục tiêu

Dựng 2 website wordpress chạy trong máy ảo ubuntu sử dụng LAMP (Linux + Apache + MySQL + PHP) và LEMP (Linux + Nginx + MySQL + PHP).

## Các bước triển khai

### 1. Với LAMP stack( Wordpress nghe port 8081)

Bước 1: Cài Apache: Cập nhật gói và cài Apache:

    sudo apt-get update
    sudo apt-get install apache2
    sudo systemctl enable apache2
    sudo systemctl start apache2


Bước 2 — Cài MySQL

     sudo apt install mysql-server -y
     sudo systemctl enable mysql
     sudo systemctl start mysql

Bảo mật:

    sudo mysql_secure_installation

Bước 3 — Cài PHP và module cần cho WordPress

     sudo apt install php libapache2-mod-php php-mysql php-curl php-gd php-xml php-mbstring php-zip php-intl -y

Kiểm tra:
  
     php -v

![alt text](/QuangAnh/Wordpress/image/image-4.png)

Bước 4 — Tạo database cho WordPress

    sudo mysql

Trong MySQL:

    CREATE DATABASE wordpress DEFAULT CHARACTER SET utf8mb4 COLLATE.utf8mb4_unicode_ci;
    CREATE USER 'wpuser'@'localhost' IDENTIFIED BY 'strongpassword';
    GRANT ALL PRIVILEGES ON wordpress.* TO 'wpuser'@'localhost';
    FLUSH PRIVILEGES;
    EXIT;

Bước 5 — Tải WordPress

     cd /var/www/html
     sudo wget https://wordpress.org/latest.tar.gz
     sudo tar -xzf latest.tar.gz
     sudo chown -R www-data:www-data wordpress
     sudo chmod -R 755 wordpress

Bước 6 — Cho Apache lắng nghe port 8081

Mở:

    sudo nano /etc/apache2/ports.conf

Thêm dòng:

    Listen 8081

Lưu lại.

Bước 7 — Cấu hình Apache cho WordPress
Tạo virtual host:

     sudo nano /etc/apache2/sites-available/wordpress.conf


Dán nội dung:

![alt text](/QuangAnh/Wordpress/image/image-3.png)

🔄 Sau khi sửa → reload Apache

    sudo systemctl reload apache2

Bước 8 — Kích hoạt site

    sudo a2ensite wordpress.conf
    sudo systemctl reload apache2

bược 9 - mở file vhost trên máy ảo vào máy thật

     sudo nano /etc/hosts

cả 2 đều thêm dòng

192.168.20.26 wp.local

**Bước 10 - Nếu làm trên Openstack thì thêm rule cho port 8081( Dễ quên)**

![alt text](/QuangAnh/Wordpress/image/image-1.png)

Bước 11: Truy cập website wordpress

![alt text](/QuangAnh/Wordpress/image/image-5.png)

![alt text](/QuangAnh/Wordpress/image/image-6.png)

### 2. Với LEMP stack( port8082 )

Bước 1 — Cài LEMP

     sudo apt update
     sudo apt install nginx mysql-server php-fpm. php-mysql php-cli php-curl php-gd php-xml. php-mbstring unzip -y
     sudo systemctl enable --now nginx mysql php7.4-fpm

 Bước 2 — Tạo database cho WordPress

     sudo mysql

xong 


     CREATE DATABASE wordpress;
     CREATE USER 'wpuser'@'localhost' IDENTIFIED BY. 'Strong@Password123';
     GRANT ALL PRIVILEGES ON wordpress.* TO. 'wpuser'@'localhost';
     FLUSH PRIVILEGES;
     EXIT;

Bước 3 — Cài PHP và module cần cho WordPress(tương tự như LAMP)


Bước 4 — Tải WordPress
cd /tmp

     wget https://wordpress.org/latest.zip
     unzip latest.zip
     sudo mv wordpress /var/www/wordpress
     sudo chown -R www-data:www-data /var/www/wordpress
     sudo find /var/www/wordpress -type d -exec chmod 755 {} \;
     sudo find /var/www/wordpress -type f -exec chmod 644 {} \;

Bước 5 — Cấu hình Nginx (port 8082)

Tạo file:

     sudo nano /etc/nginx/sites-available/wordpress

Nội dung:

![alt text](/QuangAnh/Wordpress/image/image-7.png)

Enable:

    sudo ln -s /etc/nginx/sites-available/wordpress /etc/nginx/sites-enabled/
    sudo nginx -t
    sudo systemctl reload nginx


Bước 6 — Cấu hình WordPress

     cd /var/www/wordpress
     cp wp-config-sample.php wp-config.php
     sudo nano wp-config.php

Sửa:

     define('DB_NAME', 'wordpress');
     define('DB_USER', 'wpuser');
     define('DB_PASSWORD', 'Strong@Password123');
     define('DB_HOST', 'localhost');
     $table_prefix = 'wp_';

Bước 7 - mở file vhost trên máy ảo vào máy thật( tương tự LAMP)

Bước 8 — Truy cập cài đặt

Truy cập:

     http://IP_SERVER:8082

![alt text](/QuangAnh/Wordpress/image/image-9.png)