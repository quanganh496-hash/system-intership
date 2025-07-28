# LAB STATIC ROUTING
## Data truyền từ PC1 đến PC2 thông qua Router1 và Router2
![Alt text](../imgs/LABSTATICROUTING.jpg)

## Cấu hình bài LAB
## Cấu hình IP trên Router
### Trên Router 1
Đặt tên 
> Router>enable   
Router#configure terminal   
Router(config)#hostname R1  
R1(config)# 

Cấu hình ip cho các cổng trên Router1
> R1(config)#interface serial 2/0  
R1(config-if)#ip address 192.168.1.1 255.255.255.0  
R1(config-if)#no shutdown  
R1(config-if)#exit  
R1(config)#interface fastEthernet 0/0  
R1(config-if)#ip address 192.168.2.1 255.255.255.0  
R1(config-if)#no shutdown  
R1(config-if)#exit   

Kiểm tra các ip đã cấu hình

>R1#show ip interface brief  
![Alt text](../imgs/image-1.png)

### Trên Router 2
Đặt tên 
> Router>enable 
Router#configure terminal   
Router(config)#hostname R2  
R2(config)#  

Cấu hình ip cho các cổng trên Router1  
> R2(config)#interface serial 2/0  
R2(config-if)#ip address 192.168.1.2 255.255.255.0  
R2(config-if)#no shutdown  
R2(config-if)#exit  
R2(config)#interface fastEthernet 0/0  
R2(config-if)#ip address 192.168.3.1 255.255.255.0  
R2(config-if)#no shutdown  
R2(config-if)#exit  

Kiểm tra các ip đã cấu hình

>R2#show ip interface brief  
![Alt text](../imgs/image-2.png)

## Cấu hình IP trên PC
### Trên PC1
IP Address : 192.168.2.2  
Subnet Mask : 255.255.255.0  
Default Gateway : 192.168.2.1  
![Alt text](../imgs/image-3.png)

### Trên PC2
IP Address : 192.168.3.2  
Subnet Mask : 255.255.255.0  
Default Gateway : 192.168.3.1  
![Alt text](../imgs/image-4.png)

## Cấu hình định tuyến đường đi 
### Trên Router 1
>R1(config)#route ospf 10  
R1(config-router)#network 192.168.1.0 0.0.0.255 area 0  
R1(config-router)#network 192.168.2.0 0.0.0.255 area 0  
R1(config-router)exit  
 
### Kiểm tra đường mạng 
>R1#show ip route ospf 
![Alt text](../imgs/image-5.png)

### Trên Router 2
>R2(config)#route ospf 10  
R2(config-router)#network 192.168.3.0 0.0.0.255 area 0  
R2(config-router)#network 192.168.1.0 0.0.0.255 area 0  
R2(config-router)exit  
### Kiểm tra đường mạng 
>R2#show ip route ospf  
![Alt text](../imgs/image-6.png)

## Gửi tập tin từ PC1 đến PC2
> C:\>ping 192.168.3.2  

![Alt text](../imgs/image-7.png)

PC1 đã có thể truyển Data đến PC2