# Tạo thư mục web tĩnh
Ví dụ tạo website tên myweb và đặt `file index.html` trong đó:

     sudo mkdir -p /var/www/myweb
     sudo nano /var/www/myweb/index.html

Nội dung thử:

    <h1>HELLO FROM NGINX</h1>

Phân quyền:

    sudo chown -R $USER:$USER /var/www/myweb

# Tạo file cấu hình server block (virtual host)
## Ubuntu

Tạo file:

    sudo nano /etc/nginx/sites-available/myweb.conf

Dán nội dung:

   ![alt text](image-23.png)

Kích hoạt site:

     sudo ln -s /etc/nginx/sites-available/myweb.conf /etc/nginx/ sites-enabled/

Xóa default (nếu muốn):

     sudo rm /etc/nginx/sites-enabled/default

![alt text](image-24.png)

## Rocky9
