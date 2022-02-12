### Lệnh trong Git

**Kiểm tra phiên bản Git trong cmd**

```
git --version
```

**Cấu hình môi trường làm việc**

Có 3 mức cấu hình:

- system: thông tin đc dung cho tất cả người dùng và tất cả kho chứa trên hệ thống. Thông tin được lưu ở

```
C:\Program Files\Git\mingw64\etc\gitconfig.
```

Để cấu hình cần thêm tham số --system

```
$ git config --system user.name "Van Teo"
```

Cần có quyền quản trị hệ thống mới thực hiện được cấu hình này.

- global: thông tin sẽ được dùng cho duy nhất tài khoản đang đăng nhập và tất cả các kho chứa đang làm việc trên hệ thống.

Thông tin được lưu tại ~/.gitconfig.

```
C:\Users\tentaikhoan\.gitconfig.
```

Đề cấu hình cần thêm tham số --global.

```
$ git config --global user.name "Van Teo"
```

Đây là mức hay được sử dụng.

- local: thông tin sẽ được lưu duy nhất ở 1 kho chứa.

Thông tin cấu hình được lưu duy nhất trong chính kho chứa tại .git/config.

Để cấu hình sử dụng lệnh git config 

```
 $ git config user.name "Van Teo"
```

Nếu  hệ thống được cấu hình cả 3 mức thì thông tin ở mức nào có độ ưu tiên cao hơn sẽ được sử dụng.

**Cài đặt danh tính**

```
$ git config --global user.name "Van Teo"
$ git config --global user.email nguyenvanteo@gmail.com
```

![image](https://user-images.githubusercontent.com/69178270/147443622-04ceda4a-c82a-468c-ac78-be36f418efc0.png)

Kiểm tra thông tin trong .gitconfig

![image](https://user-images.githubusercontent.com/69178270/147443725-a1c02877-d473-4002-9c50-eb9d58c92060.png)


**Kiểm tra thông số cấu hình của môi trường làm việc**

```
 git config --list
```

![image](https://user-images.githubusercontent.com/69178270/147443896-02b82363-f491-463b-a072-55b8e60757e4.png)

Để kiểm tra cụ thể một thông tin, sử dụng cú pháp sau: git config {key}

```
$ git config user.name
```

![image](https://user-images.githubusercontent.com/69178270/147443992-1f7f7467-f034-4889-b3f9-e9270a8484e1.png)

Hiển thị thông tin giúp đỡ

Muốn hiển thị thông tin trợ giúp khi cấu hình Git, sử dụng một trong ba lệnh sau (kết quả sẽ hiển thị trong cửa sổ trình duyệt):

```
– git <verb> --help
– git help <verb>
– man git -<verb>
```

Sua khi dùng $git config --help

![image](https://user-images.githubusercontent.com/69178270/147444123-3da213e8-918a-4738-8c70-e3585d010493.png)

**Tạo kho chứa từ một thư mục trên máy cục bộ**

![image](https://user-images.githubusercontent.com/69178270/147445004-250da221-13d5-4207-8d82-2df6440060d0.png)

```
cd <đường dẫn>
git init
```

Kết quả

![image](https://user-images.githubusercontent.com/69178270/147445099-30532947-8423-4a4e-b140-3371c12dd342.png)

Kiểm tra trạng thái

```
git status
```

![image](https://user-images.githubusercontent.com/69178270/147445259-041f7eab-b3d8-4bd0-a156-6b0012669bec.png)

Thực hiện theo dõi tập tin

```
git add tailieu.txt
```

![image](https://user-images.githubusercontent.com/69178270/147445418-413479c4-c32c-44c1-ba66-cee5f90ecb60.png)

Thực hiện commit đầu tiên (initial commit)

```
git commit -m 'Phiên bản đầu tiên của dự án'
```

![image](https://user-images.githubusercontent.com/69178270/147445561-0d364c03-2650-4c4f-80e3-22b2b5fe614a.png)

**Sao chép một kho chứa từ server**

```
git clone [url]
```

