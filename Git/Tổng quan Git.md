### Tìm hiểu về Git

```
Lưu lý:
- Cơ chế lưu phiên bản.
- Cơ chế theo dõi phần lập trình của mỗi cá nhân.
- Cơ chế tạo nhánh, gộp nhánh.
- Cơ chế lưu trữ kho dữ liệu từ xa (mối liên hệ giữa kho chứa cục bộ "Local respository" và kho chứa từ xa "remote respository")
```

**Hệ thống quản lý phiên bản**

Phiên bản (version) là các bản khác nhau của 1 hay nhiều tập tin, thư mục, dự án.

Trong quá trình làm việc ta có nhu cầu cao về việc khôi phục phiên bản trước đó nếu sảy ra sự cố. Sinh ra hệ thống quản lý phiên bản (Version Control System - VCS).

Một vài chức năng chính:

 - Khôi phục lại trạng thái trước đó của tập tin tại 1 thời điểm trong quá khứ.
 - Cho biết ai đã thực hiện thay đổi và thay đổi những gì.
 - Dễ dàng khôi phục trạng thái của các tập tin và tập tin bị xóa.
 - Dễ dàng thay đổi trạng thái của các tập tin theo mốc thời gian.

Chia VCS thành 3 lại:

_**1. Hệ thống cục bộ:**_ Cách làm thủ công, người dùng tự lưu trữ các phiên bản khác nhau vào những mốc thời gian khác nhau.

Nhược điểm: khó quản lý.

Sử dụng công cụ quản lý cục bộ RCS. Nó có thể lưu trữ mỗi phiên bản trong 1 thư mục, sử dụng csdl để quản lý thông tin các thư mục. Không hỗ trợ trên môi trường cộng tác nhiều người.

![image](https://user-images.githubusercontent.com/69178270/147426223-8dd3e49a-0fe0-4e34-9be4-265bff991afc.png)

_**2. Hệ thống tập trung:**_ Cho phép nhiều người cộng tác làm việc với nhau.

Hệ thống quản lý phiên bản tập trung (Centralized Version Control Systems - CVCS) Gồm máy chủ chứa tập tin và danh sách các máy khách được phép thay đổi tập tin.
Các máy khách sẽ lấy các phiên bản tập tin về từ máy chủ thực hiện các thay đổi tập tin và cập nhật lại các thay đổi tập tin lên máy chủ.

![image](https://user-images.githubusercontent.com/69178270/147426882-101f8625-3136-4893-bd1c-912eb36042ce.png)

Hạn chế: Hệ thống quản lý phiên bản tập trung, nếu mày chủ bị trục trặc sẽ khiến cho việc cập nhật bị gián đoạn hoặc toàn bộ dữ liệu bị mất.

_**3. Hệ thống phân tán:**_ 

Khắc phục hạn chế của phiên bản tập trung.

Tại đây các máy client không chỉ lấy phiên bản mới nhất từ máy chủ mà còn lấy luôn kho chứa (repository, repo) báo gồm cả lịch sử các phiên bản. Vì vậy nếu máy chủ bị trục trục trặc ta có thể lấy từ bất kì máy client nào để khôi phục.

![image](https://user-images.githubusercontent.com/69178270/147427210-437a0035-5815-4a52-a48e-b357f668bafb.png)

Cho phép client có thể liên kết với nhiều kho chứa ở xa cùng lúc.

**Nguyên tắc làm việc**

Snaphot lại toàn bộ tập tin dự án tập tin nào có tahy đổi thì lưu lại, giữ nguyên các tập tin ko thay đổi.

![image](https://user-images.githubusercontent.com/69178270/147427469-8a8db0f0-02d9-4ab9-9455-bfc5aa93486c.png)

Mỗi Snapshot tường đương với một commit trong hệ thống Git.

_Phần lớn các thao tác của git thực hiện trên máy cục bộ_ (xem phiên bản, lưu phiên bản hiện tại)

_Git đảm bảo tính toàn vẹn_ Mọi thứ đều được kiểm tra trước khi lưu vào Git. Tạo mã kiểm tra bắng cách chạy 1 thuật toán SHA.
So sánh mã SHA để xác định tập tin có bị thay đổi hay không.

_Git chỉ thêm dữ liệu_ Tạo cảm giác an toàn cho người sử dụng.

_Ba trạng thái quan trọng của tập tin_

- modifited: tập tin đã bị thay đổi (nội dung, tên) chưa lưu phiên bản (commit) trên máy cục bộ.
- staged: tập tin đã thay đổi, đã đc đánh dấu sẽ lưu lại trên máy cục bộ.
- committed: tập tin đã tahy đổi, đã đc đánh dấu và lưu trên máy cục bộ.

3 trạng thái sinh ra 3 vùng được git quản lý 

 - working tree (working directory): thư mục hiện thời, là bản sao của dự án, khu vực lm vc của lập trình viên.
 - staging area: khu vực tổ chức, là tập tin index chứa thông tin về những gì sẽ đc lưu vào lần tới.
 - .git directory: thư mục .git là nơi lưu trữ siêu dữ kiện (metadata), đây là thành phần đc sao lưu về khi nhân bản 1 kho chứa từ máy khác.

![image](https://user-images.githubusercontent.com/69178270/147429582-ecd157ed-ca67-4d1a-8635-febb67c036d8.png)



 
