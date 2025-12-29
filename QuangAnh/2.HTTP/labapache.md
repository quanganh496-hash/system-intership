# Cài đặt Apache trên CentOS / RHEL
1. Cập nhật hệ thống

    sudo yum update -y

![alt text](image-29.png)
2. Cài  Apache

     sudo dnf install httpd -y

![alt text](image-31.png)

Nếu thấy dòng:
active (running)
👉 Là Apache đang chạy.
# Cài đặt Apache trên Ubuntu
1. Cập nhật hệ thống
Trước khi cài, hãy đảm bảo hệ thống và kho package mới nhất:

       sudo apt update && sudo apt upgrade -y

2. Cài đặt Apache
Cài gói apache2:

       sudo apt install apache2 -y

3. Kiểm tra trạng thái dịch vụ
Sau khi cài xong, kiểm tra Apache có đang chạy không:

       sudo systemctl status apache2

Nếu thấy dòng:
active (running)

![alt text](image-30.png)

👉 Là Apache đang chạy.