# Thực hành Lab

## 1.Cấu hình VLAN trên SW
![image1](/HoangNH/5.TimhieuVlan/image/lab1.png)

| VLAN |  Port | 
|:-----|:------|
|VLAN10|Fa0/1, Fa0/2|
|VLAN11|Fa0/11, Fa0/12|
|VLAN12|Fa0/21,Fa0/21|

Bước 1: Tạo các VLAN

```
Switch>enable
Switch#configure terminal

Switch(config)#vlan 10
Switch(config-vlan)#name VLAN10
Switch(config-vlan)#exit

Switch(config)#vlan 11
Switch(config-vlan)#name VLAN11
Switch(config-vlan)#exit

Switch(config)#vlan 12
Switch(config-vlan)#name VLAN12
Switch(config-vlan)#exit

```

Bước 2: Gán các port vào VLAN

```
Switch>enable
Switch#configure terminal

Switch(config)#interface fastEthernet 0/1
Switch(config-if)#switchport access vlan 10
Switch(config-if)#exit

Switch(config)#interface fastEthernet 0/2
Switch(config-if)#switchport access vlan 10
Switch(config-if)#exit

Switch(config)#interface fastEthernet 0/11
Switch(config-if)#switchport access vlan 11
Switch(config-if)#exit

Switch(config)#interface fastEthernet 0/12
Switch(config-if)#switchport access vlan 11
Switch(config-if)#exit

Switch(config)#interface fastEthernet 0/21
Switch(config-if)#switchport access vlan 12
Switch(config-if)#exit

Switch(config)#interface fastEthernet 0/22
Switch(config-if)#switchport access vlan 12
Switch(config-if)#end

```

Kiểm tra:

```
Switch#show vlan

```

![image2](/HoangNH/5.TimhieuVlan/image/ktlab1.png)

Kiểm tra ping:

![image3](/HoangNH/5.TimhieuVlan/image/ping1.png)

Cùng VLAN thì ping được, khác VLAN thì không ping được.

## 2.Cấu hình VTP

![vtp](/HoangNH/5.TimhieuVlan/image/lab2.png)

| VLAN |  Port | 
|:-----|:------|
|VLAN10|192.168.10.0/24|
|VLAN20|192.168.20.0/24|

Thiết lập các VLAN:

Trên SW1:

```
Switch>enable 
Switch#configure terminal 
Switch(config)#hostname SW1
SW1(config)#

```

Tạo VLAN:

```
SW1(config)#vlan 10
SW1(config-vlan)#name VLAN10
SW1(config-vlan)#exit

SW1(config)#vlan 20
SW1(config-vlan)#name VLAN20
SW1(config-vlan)#exit

SW1(config)#

```

Gán các port vào các VLAN:

```
SW1(config)#interface fastEthernet 0/10
SW1(config-if)#switchport access vlan 10
SW1(config-if)#exit

SW1(config)#interface fastEthernet 0/11
SW1(config-if)#switchport access vlan 10
SW1(config-if)#exit

SW1(config)#interface fastEthernet 0/20
SW1(config-if)#switchport access vlan 20
SW1(config-if)#exit

SW1(config)#exit

```

Kiểm tra:

![image4](/HoangNH/5.TimhieuVlan/image/kt1.png)

Trên SW2:

```
Switch>enable 
Switch#configure terminal 
Switch(config)#hostname SW2
SW2(config)#

```

Tạo VLAN:

```

SW2(config)#vlan 10
SW2(config-vlan)#name VLAN10
SW2(config-vlan)#exit

SW2(config)#vlan 20
SW2(config-vlan)#name VLAN20
SW2(config-vlan)#exit

SW2(config)#

```

Gán các port vào VLAN:

```
SW2(config)#interface fastEthernet 0/10
SW2(config-if)#switchport access vlan 10
SW2(config-if)#exit

SW2(config)#interface fastEthernet 0/20
SW2(config-if)#switchport access vlan 20
SW2(config-if)#exit

SW2(config)#exit

```
Kiểm tra:

![image5](/HoangNH/5.TimhieuVlan/image/kt2.png)


Đặt các địa chỉ IP của SW1 cho VLAN10 và VLAN20:

```
SW1#configure terminal 
SW1(config)#interface vlan 10
SW1(config-if)#
SW1(config-if)#ip address 192.168.10.1 255.255.255.0
SW1(config-if)#no shutdown
SW1(config-if)#exit
SW1(config)#

SW1(config)#interface vlan 20
SW1(config-if)#ip address 192.168.20.1 255.255.255.0
SW1(config-if)#no shutdown 
SW1(config-if)#exit 

SW1(config)#exit
SW1#

```

Đặt các địa chỉ IP của SW2 cho VLAN10 và VLAN20:

```
SW2#configure terminal 
SW2(config)#interface vlan 10
SW2(config-if)#
SW2(config-if)#ip address 192.168.10.2 255.255.255.0
SW2(config-if)#no shutdown
SW2(config-if)#exit
SW2(config)#

SW2(config)#interface vlan 20
SW2(config-if)#ip address 192.168.20.2 255.255.255.0
SW2(config-if)#no shutdown 
SW2(config-if)#exit 

SW2(config)#exit
SW2#

```

Thiết lập cho SW1 là VTP Server và SW2 là VTP Client:

```
SW1>enable 
SW1#configure terminal 
SW1(config)#vtp mode server
SW1(config)#vtp domain NH
SW1(config)#vtp password nhanhoa2020
SW1(config)#exit

```

```
SW2>enable 
SW2#configure terminal 
SW2(config)#vtp mode client
SW2(config)#vtp domain NH
SW2(config)#vtp password nhanhoa2020
SW2(config)#exit

```

Tạo đường trunk từ SW1 đến SW2:

```
SW1#configure terminal 
SW1(config)#interface fastEthernet 0/1
SW1(config-if)#switchport mode trunk 
SW1(config-if)#end
SW1#

```

```
SW2#configure terminal 
SW2(config)#interface fastEthernet 0/1
SW2(config-if)#switchport mode trunk 
SW2(config-if)#end
SW2#

```

Kiểm tra:

```
SW# show vtp status

SW# show vtp pasword

SW# show vlan

SW# show interfaces trunk

```

![image6](/HoangNH/5.TimhieuVlan/image/show.png)