# MỤC LỤC
&ensp;[1, Install PNET](#1)

&ensp;[2. Thêm Template cho PNETLAB](#2)

![image](https://user-images.githubusercontent.com/55483458/137253306-27e89d4a-d28f-4260-bbe3-467b4bd48b82.png)

# <a name ="1">1.  Install PNET</a>
## Step 01: Download and Deploy
### Tải đĩa ảo PNET từ trang chủ về và tiến hành cài đặt.

Link: <a href="https://pnetlab.com/pages/download">https://pnetlab.com/pages/download</a>

![image](https://user-images.githubusercontent.com/55483458/137252803-cedb44b6-5316-4787-aba4-e4d829081ad2.png)

## Step 02: Register and Login

![image](https://user-images.githubusercontent.com/55483458/137252812-b51ee22c-2193-4f1f-b12f-840b27ed7a6d.png)

**Login form:**
 
![image](https://user-images.githubusercontent.com/55483458/137252864-9588dc8a-668a-4902-94cd-bef10da3a80a.png)

![image](https://user-images.githubusercontent.com/55483458/137252876-dd50d896-b3d3-4c73-affb-c52d6436e4dc.png)

## Step 03: Go to Store and Download LAB

![image](https://user-images.githubusercontent.com/55483458/137252887-8c01230f-6680-453c-ab37-816328719f00.png)

![image](https://user-images.githubusercontent.com/55483458/137253449-4bd4e296-3523-47e1-8d96-61634a6ff3f8.png)

## Step 04: Get Lab and Learn

![image](https://user-images.githubusercontent.com/55483458/137253468-05743ba0-90e0-4156-91fa-e3184fafdedb.png)

![image](https://user-images.githubusercontent.com/55483458/137253482-5a072670-ba74-4d01-b035-8c9631e3c7af.png)

![image](https://user-images.githubusercontent.com/55483458/137253490-f616a98c-756c-48aa-9641-3eca3e442b79.png)

![image](https://user-images.githubusercontent.com/55483458/137253497-e17c1ff1-95ef-4299-a58f-0134c24d24c9.png)

![image](https://user-images.githubusercontent.com/55483458/137253512-655b6bf3-d35f-4824-b8d3-fd43d8a8a1f6.png)

![image](https://user-images.githubusercontent.com/55483458/137253522-16fd2f9e-77e3-4bdb-b811-6fad72154247.png)

# <a name ="2">2. Thêm Template cho PNETLAB</a>

## 1. Cấu hình VSFTP cho PNET

### 1.1 Cài đặt vsfptd  

    $ sudo apt update
    $ sudo apt install vsftpd
    
Tiếp theo, chúng ta cần sao lưu lại cài đặt vsfptd cũ nếu bạn muốn cài đặt vsftpd mới ghi đè lên version cũ:
    
    $ sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.orig

### 1.2 Cấu hình tưởng lửa cho vsftpd
Bạn cần phải cấu hình UFW (công cụ tường lửa trên Ubuntu) để mở port cho FTP nên trước hết bạn hãy kiểm tra trạng thái hiện tại:

![image](https://user-images.githubusercontent.com/55483458/137256286-cf904867-4ecb-4bbe-ac19-0f536a18b1bd.png)

Thực hiện mở các port 20 (FTP command port), 21 (FTP data port), 990 (TLS FTP data port) và dải port 35000-40000:

    $ sudo ufw allow 20:21/tcp
    $ sudo ufw allow 990/tcp
    $ sudo ufw allow 35000:40000/tcp

![image](https://user-images.githubusercontent.com/55483458/137256348-25622c60-2890-41aa-aa76-0e7de10c6a55.png)

### 1.3 Cấu hình vsftpd
Tiếp theo bạn cần cấu hình vsftpd bằng cách mở và chỉnh sửa file cấu hình:
    
    $ sudo nano /etc/vsftpd.conf

Để giới hạn chỉ cho người dùng nội bộ truy cập vào FTP thì bạn thêm dòng cấu hình sau:

    anonymous_enable=NO
    local_enable=YES

Bạn cần cho phép quyền ghi để có thể kích hoạt chức năng upload trên FTP Server. Để làm điều đó, uncomment dòng sau:

    write_enable=YES

Tiếp theo cần giới hạn người dùng chỉ có thể thao tác trên thư mục cụ thể. Để làm điều đó, bạn cần uncomment dòng sau:

    chroot_local_user=YES
    allow_writeable_chroot=YES

VSftpd có thể sử dụng bất kì port nào cho các kết nối passive FTP. Vi vậy nên chúng ta thực hiện cấu hình minimum port và maximum port với dòng cấu hình sau:

    pasv_min_port=35000
    pasv_max_port=
    
Cuối cùng là để giới hạn những người dùng nào có thể đăng nhập vào FTP Server, thêm đoạn cấu hình sau:

    userlist_enable=YES
    userlist_file=/etc/vsftpd.userlist
    userlist_deny=NO

Với đoạn cấu hình trên, bạn đã chỉ định người dùng có thể truy cập với username lưu tại **/etc/vsftpd.userlist**.

### 1.4 Cấu hình thư mục người dùng

Để thêm người dùng mới vào FTP Server, trong bài viết mình sẽ thực hiện thêm mới người dùng. Đầu tiên là tạo người dùng mới:

    $ sudo adduser ftpuser
    $ sudo passwd ftpuser

Tiếp theo bạn cần thêm người dùng mới tạo vào danh sách người dùng của FTP:

    $ echo "ftpuser" | sudo tee -a /etc/vsftpd.userlist

Sau khi thêm vào danh sách, bạn hãy tạo thư mục cho người dùng đó:

    $ sudo mkdir /home/ftpuser/ftp
    $ sudo chown nobody:nogroup /home/ftpuser/ftp
    $ sudo chmod a-w /home/ftpuser/ftp
  
Sau khi tạo xong thư mục, kiểm tra lại quyền thư mục như sau:  

    $ sudo ls -al /home/ftpuser/ftp
    total 8
    dr-xr-xr-x 2 nobody   nogroup  4096 Jun  7 13:08 .
    drwxr-xr-x 3 ftpuser ftpuser 4096 Jun  7 13:08 ..

Tiếp theo, bạn cần tạo thư mục có quyền write để có thể lưu các file tải lên:

    $ sudo mkdir /home/ftpuser/ftp/upload
    $ sudo chown ftpuser:ftpuser /home/ftpuser/ftp/upload

Lúc đó, thư mục dành cho việc tải lên sẽ có quyền như bên dưới:

    $ sudo ls -al /home/ftpuser/ftp
    total 12
    dr-xr-xr-x 3 nobody   nogroup  4096 Jun  7 13:10 .
    drwxr-xr-x 3 ftpuser ftpuser 4096 Jun  7 13:08 ..
    drwxr-xr-x 2 ftpuser ftpuser 4096 Jun  7 13:10 upload
    
### 1.5 Kiểm tra kết nối FTP 

Ở đây mình sử dụng phần mềm WinSCP để kết nối VSFTP tới PNET

Chúng ta sẽ tiến hành kết nối tới địa chỉ IP của PNET 

![image](https://user-images.githubusercontent.com/55483458/137257275-37ab4406-3a0f-4c92-8a86-55242293f4b0.png)

![image](https://user-images.githubusercontent.com/55483458/137257281-85329f1b-9bd8-48ce-977c-2db142f619df.png)

Đây là màn hình khi chúng ta kết nối thành công

![image](https://user-images.githubusercontent.com/55483458/137257487-510e4331-f42a-4dbc-82ac-30cedb324a61.png)

## 2. Tải và cài đặt template CISCO IOU

Các bạn tiến hành download các template bên trái theo link sau đây: 

**https://drive.google.com/drive/folders/1FT1l4bl-jZ3p_kzEVYFSS8I2zq0TvxdJ**

Từ màn hình bên phải của WinSCP, các bạn vào theo đường dẫn **/opt/unetlab/addons/iol/bin/**

![image](https://user-images.githubusercontent.com/55483458/137257821-9e2a5a9b-ba18-4a83-a58a-44682add9064.png)

Tiến hành upload file từ Client sang máy chủ PNETLAB

![image](https://user-images.githubusercontent.com/55483458/137257943-b02d088b-baa6-42c8-9080-011ce829e860.png)

Từ đây chúng ta chuyển sang màn hình console của PNETLAB và tiến hành cấu hình cho template. Các bạn làm theo lệnh sau:

    cd /opt/unetlab/addons/iol/bin/
    
    
    chmod +x CiscoIOUKeygen.py
    python CiscoIOUKeygen.py
    
=>  Lệnh này thêm quyền execute (thực thi) cho files CiscoIOUKeygen.py và tạo key cho IOU

![image](https://user-images.githubusercontent.com/55483458/137258356-37232aa7-3eca-4e6c-9477-c9d31ab0e79b.png)

Sau khi thực hiện xong màn hình sẽ xuất hiện như trên. Các bạn gõ theo hướng dẫn đã xuất hiện, Thêm key license vào ~/.iourc

    # nano ~/.iourc
    
    
![image](https://user-images.githubusercontent.com/55483458/137258522-cd2c9a69-5936-4466-a1af-97f713c3cdd4.png)

Tiếp theo ta nhập lệnh:

    /opt/unetlab/wrappers/unl_wrapper -a fixpermissions

=>  Lệnh này fix lại phân quyền

### Vậy là chúng ta đã cài đặt xong template :D Việc còn lại là khởi động lại máy chủ PNET sau đó tiến hành truy cập vào Web Console và tạo LAB thôi !!!! 

![image](https://user-images.githubusercontent.com/55483458/137258650-059cb311-e481-440a-9d76-4a9d91f84027.png)

## CHÚC CÁC BẠN MAY MẮN !!!!
