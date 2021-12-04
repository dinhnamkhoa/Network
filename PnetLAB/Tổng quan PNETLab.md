### Tìm hiểu về PNETLab

### Muc lục

[Tổng quan](#1)

&ensp;[Giới thiệu](#1.1)

&ensp;[Những phần mềm và nền tảng ảo hỗ trợ](#1.2)

&ensp;[Phần cứng và hệ thống không hỗ trợ](#1.3)

&ensp;[Một số đặc điểm](#1.4)

[Cơ chế hệ thống của PNETLab](#2)

[Quản lý tài khoản Offline](#3)

[Quản lý tài khoản Online](#4)

[Nâng cấp PNETLab](#5)

### <a name="1"> Tổng quan </a>

PNETLab (Packet Network Emulator Tool Lab) là một nền tảng cho phép bạn tải xuống và chia sẻ lab với cộng đồng.

![image](https://user-images.githubusercontent.com/69178270/137084613-eb89dff1-74d7-4bea-83d8-f744e83b49e5.png)

<a name="1.1"> **Giới thiệu** </a>

Bao gồm PNETLab Box và PNETLab store:

 - PNETLab Box (với hai chế độ: Ngoại tuyến và Trực tuyến)) là một máy ảo. Nó được cài đặt trên máy cục bộ và Lab sẽ chạy trên đó, vì vậy bạn không phải lo lắng về tốc độ của phòng thí nghiệm.

 - PNETLab Store là một nền tảng web với hàng trăm Lab miễn phí trong các lĩnh vực mạng, cơ sở dữ liệu, hệ thống ... Tất cả những gì bạn cần làm là tải lab và học (IOS, Docker được bao gồm trong lab khi bạn tải xuống từ PNETLab)

![image](https://user-images.githubusercontent.com/69178270/137084821-98600f76-f49d-4b97-98b4-df607710c67b.png)

<a name="1.2"> **Những phần mềm và nền tảng ảo hỗ trợ** </a>

 -	VMware Workstation 12.5 or later.
 
 -	VMware Player 12.5 or later.
 
 -	VMware ESXi 6.0 or later.
 
 -	Ubuntu Server 16.04 LTS as platform for bare metal (roadmap).
 
 -	Google Cloud Platform.

<a name="1.3"> **Phần cứng và hệ thống không hỗ trợ** </a>

 -	AMD CPU based PC or Server.

 -	VirtualBox virtualization.

 -	Citrix XenServer.

 -	Microsoft HyperV.

 -	Ubuntu 17.X or 18.x as platform.

<a name="1.4"> **Một số đặc điểm** </a>

 - Có phiên bản Offline
  
 - Miễn phí         
 
 - Hỗ trợ Lab Store, Device Soter, …

 - Hỗ trợ nhiều hệ điều hành (Cisco, Juniper, Arista,…)

 - Quyền người dùng

 - Các đặc điểm hỗ trợ làm Lab (Task, Timer,…)

 - Không giới hạn số Node ở mỗi Lab

 - 3D Model

 - Có thể quản lý lượng RAM, CPU, HDD sử dụng cho từng thiết bị

 - Cấu hình Proxy

 - Icon đẹp, có thể tùy chỉnh

 - Hỗ trợ Wireshark Capture, Telnet, Hot connections, NAT cloud,…

### <a name="2"> Cơ chế hệ thống của PNETLab </a>

Gồm 2 mode : Offline Mode và Online Mode

![image](https://user-images.githubusercontent.com/69178270/137245462-480d79fd-44c4-430e-a7e1-acd9f4a58d07.png)

![image](https://user-images.githubusercontent.com/69178270/137245515-5049ade9-d5a9-4183-9bb7-c5ef4521cc20.png)

 -	Khi nhấn vào Online Mode : Online Mode sẽ được kích hoạt và Offline Mode sẽ bị vô hiệu. Chế độ mặc định sẽ được chuyển thành Online.
 
 -	Khi nhấn vào Offline Mode : Offline Mode sẽ được kích hoạt và Online Mode sẽ bị vô hiệu. Chế độ mặc định sẽ được chuyển thành Offline. Tài khoản mặc định sẽ là : admin/pnet.
 
![image](https://user-images.githubusercontent.com/69178270/137245560-d5b4a326-99b6-497e-94c8-e00eee5f5af0.png)

Để quản lý System Mode : **System -> System Mode**

![image](https://user-images.githubusercontent.com/69178270/137245611-2b3a8567-8504-476f-abc3-7726bf06996f.png)

 -	Người dùng có thể tùy chỉnh chế độ đăng nhập mặc định, vô hiệu hoặc kích hoạt các chế độ.

 - Hệ thống cũng hỗ trợ chuyển chế độ bằng câu lệnh:

   *	Để thay đổi chế độ mặc định sử dụng câu lệnh : **mode default online** hoặc **mode default offline**.
 
   *	Để cài lại mật khẩu offline sử dụng câu lệnh : **mode reset offline**.

   *	Để cài lại chế độ của hệ thống sang nguyên bản sử dụng câu lệnh : **mode reset all**.

### <a name="3"> Quản lý tài khoản Offline </a>

Tạo Role và tài khoản người dùng tại : **Accounts**

![image](https://user-images.githubusercontent.com/69178270/137245992-2de540cd-842c-4c95-bd93-8a8468acdf24.png)

 -	Có thể tạo tối đa 10 tài khoản.
 
 -	Tài khoản Offline sẽ có tag    và tài khoản Online sẽ có tag 🌍. Bạn không thể tùy chỉnh tài khoản Online
 
 -	Để thêm tài khoản nhấn vào nút Add ➕
 
 -	Cần ít nhất là username, password và role
 
 -	Có thể đặt thời gian kích hoạt hoặc hết hạn cho từng tài khoản.

![image](https://user-images.githubusercontent.com/69178270/137246116-4842ad79-e1ca-40c7-833a-64e1eb941602.png)

### <a name="4"> Quản lý tài khoản Online </a>

Cũng như tài khoản Offline, để tạo tài khoản Online và Role : **Accounts**

![image](https://user-images.githubusercontent.com/69178270/137246196-32d2c62c-08e6-4bb6-bc8a-715ae5e929b9.png)

 -	Có thể tạo tối đa 10 tài khoản.
 
 -	Tài khoản Offline sẽ có tag    và tài khoản Online sẽ có tag 🌍. Bạn không thể tùy chỉnh tài khoản Online
 
 -	Để thêm tài khoản nhấn vào nút Add ➕

 -	Cần email, và role.

 -	Có thể đặt thời gian kích hoạt hoặc hết hạn cho từng tài khoản.
 
![image](https://user-images.githubusercontent.com/69178270/137246266-b5fa92ca-563f-4f32-98a1-0c6aa1ab4e12.png)

### <a name="5"> Nâng cấp PNETLab </a>

**PNETLab có kết nối mạng:**

![image](https://user-images.githubusercontent.com/69178270/137246384-a5debaca-87cb-4f24-9df5-2cf1f1b9c61f.png)

Để nâng cấp phiên bản mới nhất : **System > Version > Upgrade**

**PNETLab không có kết nối mạng:**

B1: Vào trang chủ để tải những gói nâng cấp.

B2: Người dùng phải nâng cấp từng bước một từ phiên bản hiện tại đến phiên bản mới nhất ( VD 1.0.1 > 1.0.2 > 1.0.3. Không thể nâng cấp từ 1.0.1 > 1.0.3,có thể gây ra lỗi )

B3: Sau khi tải gói nâng cấp. Sao chép nó tới thư mục /tmp của PNETLab.

B4: Khởi động PNETLab và đăng nhập bằng tài khoản root và chạy câu lệnh để kiểm tra:

 **. cd /tmp**
	
 **. ls -l**

B5: Giải nén gói nâng cấp bằng lệnh:
	
 . Xóa gói nâng cấp cũ nếu có : **rm -rf upgrade**
	
 . **unzip [package] -d ./upgrade** ( VD : unzip 4.0.1.zip -d ./upgrade)
	
 . Kiểm tra lại bằng câu lệnh : **ls -l** . Sẽ thấy thư mục nâng cấp.

![image](https://user-images.githubusercontent.com/69178270/137246564-9933e6d8-b6d5-4911-9d32-c910548171d2.png)

![image](https://user-images.githubusercontent.com/69178270/137246573-63020db3-f8d2-4bee-82c5-ee8315543fa2.png)

B6: Chạy những câu lệnh để nâng cấp:
	
 **. chmod 755 -R upgrade**
	
 **. find upgrade -type f -print0 | xargs -0 dos2unix 2>&1**
	
 **.  ./upgrade/upgrade**
 
![image](https://user-images.githubusercontent.com/69178270/137246637-6a4eaee5-c435-4d2e-90fa-cc7076881925.png)

![image](https://user-images.githubusercontent.com/69178270/137246652-ff4847c8-8427-4f74-bfca-b8d3f501c2f6.png)

B7: Đăng nhập vào trang Web và kiểm tra.
