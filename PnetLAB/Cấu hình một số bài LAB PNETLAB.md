# CẤU HÌNH MỘT SỐ BÀI LAB PNET:

# MỤC LỤC


&ensp;[1. Subnetting Summarization Static Routing and ACLs !](#1)

&ensp;[2. Static Routing and DNS](#2)

&ensp;[3. EIGRP Summarization Static NAT ACLs](#3)

&ensp;[4. Multi- Area OSPF LAN Switching](#4)

&ensp;[5. EIGRP PAT ACLs and Banners](#5)

&ensp;[6. VTP STP and OSPF](#6)

&ensp;[7. DHCP InterVLAN routing and RIPv2](#7)

# <a name="1">1.  Subnetting Summarization Static Routing and ACLs ![](.//media/image13.png)</a>

## Thay đổi Hostname và cấu hình IP, loopback interfack

![](.//media/image14.png)


![](.//media/image15.png)


-   Ta sẽ làm tương tự với R3

##  Cấu hình single static route 

R1:

![](.//media/image16.png)


R3:

![](.//media/image17.png)


## Cấu hình ACL trên R1 dựa theo yêu cầu

![](.//media/image18.png)



![](.//media/image19.png)

## Cấu hình ACL trên R2 dựa theo yêu cầu

![](.//media/image20.png)
  

![](.//media/image21.png)

# <a name="2">2.  Static Routing and DNS</a>

![](.//media/image22.png)

## Change Hostname

![](.//media/image23.png)


-   Làm tương tự với các thiết bị khác

## Tạo VLAN và cấu hình cho VLAN trên SW1

![](.//media/image24.png)


![](.//media/image25.png)


![](.//media/image26.png)


![](.//media/image27.png)


-   Ở đây chúng ta tạo vlan2, gán tên cho vlan. Sau đó gán địa chỉ IP
    cho vlan2 và gán porte0/2 vào vlan đồng thời set default-gateway cho
    switch để các thiết bị khác có thể kết nối được

## Cấu hình địa chỉ IP cho các router

-   R1:

![](.//media/image28.png)


-   R2:

![](.//media/image29.png)


-   R3:

![](.//media/image30.png)


## Cấu hình static route 

-   R1:

![](.//media/image31.png)


-   R2:

![](.//media/image32.png)
![](.//media/image32.png)


![](.//media/image32.png)
![](.//media/image33.png)


-   Khi cấu hình xong chúng ta sẽ thấy các mạng đã thông nhau

![](.//media/image34.png)

# <a name="3">3.  EIGRP Summarization Static NAT ACLs</a>

![](.//media/image35.png)

## Change Hostname

![](.//media/image23.png)


-   Làm tương tự với các thiết bị khác

## Tạo VLAN và cấu hình cho VLAN trên SW1

![](.//media/image24.png)


![](.//media/image25.png)


![](.//media/image26.png)


![](.//media/image27.png)


-   Ở đây chúng ta tạo vlan2, gán tên cho vlan. Sau đó gán địa chỉ IP
    cho vlan2 và gán porte0/2 vào vlan đồng thời set default-gateway cho
    switch để các thiết bị khác có thể kết nối được

## Cấu hình địa chỉ IP cho các router

-   R1:

![](.//media/image28.png)


-   R2:

![](.//media/image29.png)


-   R3:

![](.//media/image30.png)


## Cấu hình EIGRP AS 254 cho các router

-   R1:

![](.//media/image36.png)


-   R2:

![](.//media/image37.png)


-   R3:

![](.//media/image38.png)


## Cấu hình summary eigrp cho 3 loopback interfafce trên R1

![](.//media/image39.png)
![](.//media/image39.png)


-   Kiểm tra R2 và R3 có single route tới 3 interface loopback

> ![](.//media/image40.png)
>
> ![](.//media/image41.png)
>
> ![](.//media/image42.png)
>
> ![](.//media/image43.png)

## Cấu hinh NAT trên R3 và telnet trên SW1, đảm bảo mọi thiết bị truy cập được từ địa chỉ NAT

-   R3:

![](.//media/image44.png)


![](.//media/image45.png)

-   SW1:

![](.//media/image46.png)


-   Kiểm tra kết nối:

![](.//media/image47.png)


# <a name="4">4.  Multi- Area OSPF LAN Switching<a/>

![](.//media/image48.png)

## Change Hostname

![](.//media/image23.png)


-   Làm tương tự với các thiết bị khác

## Tạo VLAN và cấu hình cho VLAN trên SW1

![](.//media/image49.png)


![](.//media/image50.png)


![](.//media/image51.png)


![](.//media/image52.png)


![](.//media/image53.png)

## Cấu hình địa chỉ IP cho các router

-   R1:

![](.//media/image54.png)

![](.//media/image55.png)


-   R2:

![](.//media/image56.png)


-   R3:

![](.//media/image57.png)


![](.//media/image58.png)


-   R4:

![](.//media/image59.png)


## Cấu hình OSPF theo từng area cho từng router

-   R1:

![](.//media/image60.png)


-   R2:

![](.//media/image61.png)


-   R3:

![](.//media/image62.png)


-   R4:

![](.//media/image63.png)

-   Kiểm tra kết nối

![](.//media/image64.png)

![](.//media/image65.png)

  # <a name="5">5.  EIGRP PAT ACLs and Banners</a>

![](.//media/image66.png)


## Change Hostname

![](.//media/image23.png)


-   Làm tương tự với các thiết bị khác

## Tạo VLAN và cấu hình cho VLAN trên SW1

![](.//media/image67.png)


![](.//media/image68.png)

## Cấu hình địa chỉ IP cho các router

-   R1:

![](.//media/image69.png)


-   R2:

![](.//media/image70.png)


-   R3:

![](.//media/image71.png)


-   R4:

![](.//media/image72.png)


## Cấu hình EIGRP AS 2000 cho từng router

-   R1:

![](.//media/image73.png)


-   R2:

![](.//media/image74.png)


-   R3:

![](.//media/image75.png)


## Cấu hình static route cho R4 - banner & Telnet cho R1 và R3

-   R4:

![](.//media/image76.png)


-   R1:

![](.//media/image77.png)


-   R3:

![](.//media/image78.png)


## Cấu hình PAT trên R2 cho ping traffic

![](.//media/image79.png)

![](.//media/image80.png)


-   Kiểm tra kết nối:

![](.//media/image81.png)

## Cấu hình PAT trên R2 cho Telnet Traffic

![](.//media/image79.png)
![](.//media/image79.png)


![](.//media/image82.png)

-   Kiểm tra kết nối:

![](.//media/image83.png)


  # <a name="6">6.  VTP STP and OSPF</a>

## Change Hostname

![](.//media/image23.png)


-   Làm tương tự với các thiết bị khác

## Cấu hình VTP cho SW1 và SW2

-   SW1:

![](.//media/image84.png)


![](.//media/image85.png)

-   SW2:

![](.//media/image86.png)


![](.//media/image87.png)

## Cấu hình VLAN trên SW1 và SW2

-   SW1:

![](.//media/image88.png)


![](.//media/image89.png)

![](.//media/image90.png)

-   SW2:

![](.//media/image91.png)


![](.//media/image92.png)


![](.//media/image93.png)

## Cấu hình Trunking cho SW1 và SW2

![](.//media/image94.png)


![](.//media/image95.png)

![](.//media/image96.png)

## Cấu hình địa chỉ IP cho các router

-   R1:

![](.//media/image97.png)


-   R4:

![](.//media/image98.png)


## Cấu hình STP -- SW1 là Root Bridge cho VLAN 4010 và 4030 với priority 4096, SW2 làm Root Bridge cho VLAN 4020 và 4040 

-   SW1:

![](.//media/image99.png)


![](.//media/image100.png)

![](.//media/image101.png)

-   SW2:

![](.//media/image99.png)


![](.//media/image102.png)

![](.//media/image103.png)

## Cấu hình OSPF cho R1 và R4

-   R1:

![](.//media/image104.png)


![](.//media/image105.png)

-   R4:

![](.//media/image106.png)


![](.//media/image107.png)

-   Kiểm tra kết nối

![](.//media/image108.png)

![](.//media/image109.png)

  # <a name="7">7.  DHCP InterVLAN routing and RIPv2</a>

![](.//media/image110.png)

## Change hostname 

![](.//media/image111.png)


## Create VLAN ( SW1)

![](.//media/image112.png)


![](.//media/image113.png)

## Config VTP

SW1:

![](.//media/image114.png)
![](.//media/image115.png)


SW2:

![](.//media/image116.png)


![](.//media/image117.png)


Sau khi cấu hình vtp, SW2 sẽ có bảng vlan sau:

![](.//media/image118.png)

## Cấu hình Trunking cho e0/2 và gán VLAN20 cho SW1 , gán VLAN 30 cho e0/2 và VLAN 30 cho e0/3 của SW2

SW1:

![](.//media/image119.png)


![](.//media/image120.png)


SW2:

![](.//media/image121.png)


## Cấu hình IP, VLAN

R2:

![](.//media/image122.png)


R4:

![](.//media/image123.png)


SW1:

![](.//media/image124.png)


![](.//media/image125.png)


SW2:

![](.//media/image126.png)

![](.//media/image127.png)


## Cấu hình subinterface

![](.//media/image128.png)


![](.//media/image129.png)


![](.//media/image130.png)

## Cấu hình DHCP Server cho R1

![](.//media/image131.png)


Chúng ta vào R3 để thiết lập nhận ip dhcp

![](.//media/image132.png)
