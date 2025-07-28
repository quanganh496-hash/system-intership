# 1. Cấu hình SW: đặt IP cho SW

# 2. Cấu hình VLAN trên SW

![hinh](/LinhNH/05.Timhieu_VLAN_Trunking/images/anh1.png)


Mặc định, thì tất cả các cổng (port) trên switch đều nằm trong cùng VLAN có ID là 1 (VLAN 1)

__Tạo các VLAN10, VLAN11, VLAN12__

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

Kiểm tra lại VLAN vừa tạo:

![hinh](/LinhNH/05.Timhieu_VLAN_Trunking/images/anh2.png)

3 VLAN đã được khởi tạo. Tuy nhiên, chưa có port nào được gán vào vlan.

__Gán các port vào VLAN đã định trước__

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

Kiểm tra các port gán đúng vlan chưa

    Switch#show vlan

![hinh](/LinhNH/05.Timhieu_VLAN_Trunking/images/anh3.png)

Kiểm tra ping từ các PC trong cùng VLAN -> OK  
Ping giữa các VLAN khác nhau -> Không ping được.

![hinh](/LinhNH/05.Timhieu_VLAN_Trunking/images/anh4.png)


# 3. Cấu hình VTP

## VTP config

![hinh](/LinhNH/05.Timhieu_VLAN_Trunking/images/anh5.png)

Quy hoạch VLAN:

- VLAN10 : 192.168.10.0/24
- VLAN20 : 192.168.20.0/24

__Cấu hình VTP__
1. Đặt IP cho các PC theo phân hoạch
2. Thiết lập các VLAN trên 2 SW

_Trên SW1_

Đặt tên:

    Switch>enable 
    Switch#configure terminal 
    Switch(config)#hostname SW1
    SW1(config)#

Tạo 2 VLAN10 và VLAN20:

    SW1(config)#vlan 10
    SW1(config-vlan)#name VLAN10
    SW1(config-vlan)#exit

    SW1(config)#vlan 20
    SW1(config-vlan)#name VLAN20
    SW1(config-vlan)#exit

    SW1(config)#

Gán các port vào đúng các VLAN định sẵn:

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

Kiểm tra lại:

![hinh](/LinhNH/05.Timhieu_VLAN_Trunking/images/anh6.png)

_Trên SW2_

Đặt tên:

    Switch>enable 
    Switch#configure terminal 
    Switch(config)#hostname SW2
    SW2(config)#

Tạo 2 VLAN10 và VLAN20:

    SW2(config)#vlan 10
    SW2(config-vlan)#name VLAN10
    SW2(config-vlan)#exit

    SW2(config)#vlan 20
    SW2(config-vlan)#name VLAN20
    SW2(config-vlan)#exit

    SW2(config)#

Gán các port vào đúng các VLAN định sẵn:

    SW2(config)#interface fastEthernet 0/10
    SW2(config-if)#switchport access vlan 10
    SW2(config-if)#exit

    SW2(config)#interface fastEthernet 0/20
    SW2(config-if)#switchport access vlan 20
    SW2(config-if)#exit

    SW2(config)#exit
Kiểm tra lại:

![hinh](/LinhNH/05.Timhieu_VLAN_Trunking/images/anh7.png)

__Đặt IP cho các interface VLAN trên 2 SW__  
Đặt các địa chỉ IP của SW1 cho VLAN10 và VLAN20:

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

Đặt các địa chỉ IP của SW2 cho VLAN10 và VLAN20:

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

__Thiết lập VTP Server và VTP Client__

Mặc định thì Catalyst switch sẽ được cấu hình làm VTP Server. Thiết lập cho SW1 là VTP Server và SW2 là VTP Client

    SW1>enable 
    SW1#configure terminal 
    SW1(config)#vtp mode server
    SW1(config)#vtp domain NH
    SW1(config)#vtp password nhanhoa2020
    SW1(config)#exit

    SW2>enable 
    SW2#configure terminal 
    SW2(config)#vtp mode client
    SW2(config)#vtp domain NH
    SW2(config)#vtp password nhanhoa2020
    SW2(config)#exit

Tạo đường trunk từ SW1 đến SW2:
    SW1#configure terminal 
    SW1(config)#interface fastEthernet 0/1
    SW1(config-if)#switchport mode trunk 
    SW1(config-if)#end
    SW1#

    SW2#configure terminal 
    SW2(config)#interface fastEthernet 0/1
    SW2(config-if)#switchport mode trunk 
    SW2(config-if)#end
    SW2#

Câu lệnh kiểm tra

    SW# show vtp status

    SW# show vtp pasword

    SW# show vlan

    SW# show interfaces trunk 

![hinh](/LinhNH/05.Timhieu_VLAN_Trunking/images/anh8.png)
