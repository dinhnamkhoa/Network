### Thao tác với kho chứa

Tập tin đã được theo dõi là tập tin đã có mặt trong snapshot trước, nghĩa là được được commit ít nhất một lần. 

Tập tin được theo dõi có thể ở các tình trạng: unmodified (chưa bị thay đổi), modified (đã bị thay đổi), hoặc đã được đánh dấu để commit (staged).

Tập tin chưa được theo dõi là các tập tin còn lại, bao gồm các tập tin trong kho chứa mà không có ở snapshop trước (chưa được commit lần nào) hoặc chưa được đánh dấu để commit (chưa được stage). Ví dụ, các tập tin vừa được tạo sẽ là tập tin chưa được theo dõi.

Khi mới clone một kho chứa thì mọi tập tin trong kho chứa sẽ ở trạng thái tracked và unmodified.

Stage các tập tin vừa bị thay đổi này, sau đó commit các tập tin, quá trình này được lặp đi lặp lại liên tục.

![image](https://user-images.githubusercontent.com/69178270/147446496-4f1cec7b-44e4-4e3a-8486-814dc752deaa.png)

**Kiểm tra trạng thái của tập tin**

```
$ git status
```
**Theo dõi các tập tin mới**

```
$ git add readme.txt
```

**Quản lý các tập tin đã thay đổi**

```
vutru@HUYVU MINGW64 /f/TextGit (master)
$ git add Text1.txt

vutru@HUYVU MINGW64 /f/TextGit (master)
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   Text1.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   Text1.txt


vutru@HUYVU MINGW64 /f/TextGit (master)
$ git commit -m Text1.txt
[master (root-commit) 1c214f2] Text1.txt
 1 file changed, 1 insertion(+)
 create mode 100644 Text1.txt

vutru@HUYVU MINGW64 /f/TextGit (master)
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   Text1.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Text2.txt

no changes added to commit (use "git add" and/or "git commit -a")

vutru@HUYVU MINGW64 /f/TextGit (master)
$ git add Text2.txt

vutru@HUYVU MINGW64 /f/TextGit (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   Text2.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   Text1.txt


vutru@HUYVU MINGW64 /f/TextGit (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file:   Text2.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   Text1.txt


vutru@HUYVU MINGW64 /f/TextGit (master)
$ git add Text1.txt

vutru@HUYVU MINGW64 /f/TextGit (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   Text1.txt
        new file:   Text2.txt


vutru@HUYVU MINGW64 /f/TextGit (master)
$
```

**Hiển thị trạng thái ở dạng rút gọn**

```
$ git status -s
```

![image](https://user-images.githubusercontent.com/69178270/147447352-d8bf55e5-4f52-4c21-8a75-9296c504f6e8.png)

 - ?? là tập tin chưa được theo dõi (untracked)
 - A là tập tin đã được đánh dấu để commit (staged) 
 - M là tập tin đã bị thay đổi mà chưa được đánh dấu (modified)
 - AM là tập tin đã staged và modified
 - MM là tập tin đã modified, đã staged rồi lại modifed.

**Bỏ qua các tập tin**

– Dòng trống hoặc bắt đầu với dấu # sẽ bị bỏ qua

– *.a : yêu cầu Git bỏ qua tất cả các tập tin có phần mở rộng là a

– *.[oa] : yêu cầu Git bỏ qua các tập tin có phần mở rộng là o hoặc a (a là tập tin archive, o là tập tin object, là các tập tin được sinh ra trong quá trình biên dịch mã nguồn)

– Sử dụng dấu ! để phủ định các giá trị phía sau, ví dụ "!lib.a" nghĩa là không bỏ qua tập tin lib.a

– Dấu * đại diện cho 0 hoặc nhiều kí tự

– Dấu ? đại diện cho một kí tự

– [0-9] đại diện cho một khoảng dữ liệu từ 0 tới 9

– Bắt đầu một luật bằng dấu xuyệt (/) để tránh đệ quy

– Kết thúc một luật bằng dấu xuyệt (/) để xác định một thư mục

**Xem các thay đổi staged và unstaged**

Kiểm tra xem thay đổi nội dung nào trong tài liệu

```
git diff
```

![image](https://user-images.githubusercontent.com/69178270/147449729-a617c956-052c-4d63-a53d-c962c39d3d20.png)


Nếu muốn biết những nội dung nào đã được staged để commit, thì sử dụng lệnh git diff với tham số là --cached hoặc --staged. Lệnh này sẽ thực hiện so sánh nội dung của tập tin trong staging với tập tin đã được commit lần trước đó.

```
$ git diff --staged
```

**Commit thay đổi**

```
$ git commit
```

![image](https://user-images.githubusercontent.com/69178270/147450461-a0eed458-3a66-4289-b06c-1354d1a598ec.png)

Bạn cũng có thể sử dụng lệnh git commit -v để đưa nội dung của lệnh git diff --staged vào trong cửa sổ soạn thảo.

```
git commit -v
```

Ngoài ra, cũng có thể nhập trực tiếp thông điệp của mỗi commit bằng tham số -m.

```
git commit -m “Issue số 2, có sửa hàm abc()”
```

**Bỏ qua khu vực tổ chức**

Để thực hiện, bạn sử dụng thêm tham số -a trong lệnh commit, Git sẽ tự động thêm tất cả các tập tin đã được theo dõi, trước khi thực hiện commit.

```
$ git commit -a -m "test commit khong can git add"
```

![image](https://user-images.githubusercontent.com/69178270/147451029-2a212ec6-c890-4ba9-aa5f-e6217f11b44f.png)

**Xóa tập tin**

```
$ git rm code.php
```

```
$ git commit -m "xóa tập tin code.php"
```

```
vutru@HUYVU MINGW64 /f/TextGit (master)
$ git rm Text2.txt
rm 'Text2.txt'

vutru@HUYVU MINGW64 /f/TextGit (master)
$ git status
On branch master
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    Text2.txt


vutru@HUYVU MINGW64 /f/TextGit (master)
$ git commit -m Text2.txt
[master 34fe41b] Text2.txt
 1 file changed, 10 deletions(-)
 delete mode 100644 Text2.txt

vutru@HUYVU MINGW64 /f/TextGit (master)
$ git status
On branch master
nothing to commit, working tree clean

vutru@HUYVU MINGW64 /f/TextGit (master)
$ git status -s
```


Một số lệnh xóa

```
$ git rm -f xoa.txt với tập tin thuộc A, ??

git rm --cached cached.txt xóa khỏi theo dõi 

$ git rm -r thumuc/ xóa thư mục

$ git rm log/*.log xóa toàn bộ các tập tin có phần mở rộng .log

$ git rm \*~ xóa toàn bộ tập tin có phần kết là ~

$ rm –r tenthumuc xóa thư mục trong thư mục làm việc

```

![image](https://user-images.githubusercontent.com/69178270/147451971-180a28b5-bc28-46f0-a018-80dd148053f1.png)

**Đổi tên tập tin**

```
$ git mv taptin1.doc taptin2.doc
```

![image](https://user-images.githubusercontent.com/69178270/147452379-fe31556d-4064-4275-a39f-58c043b93330.png)


**Xem lịch sử commit**


```
$git log
```

![image](https://user-images.githubusercontent.com/69178270/147452495-c7d079da-d1bc-44e7-902b-0a29a9bd4ae6.png)

```
Tham số -p sẽ hiển thị diff của từng commit, sử dụng thêm tham số -2 để chỉ hiển thị 2 commit gần nhất.

$ git log -p -2
```

![image](https://user-images.githubusercontent.com/69178270/147452599-92ba5a66-88dd-4511-bee1-46a2651a8a25.png)

```
Đối với văn bản lớn, có thể sử dụng thêm tham số --word-diff để xem thông tin một cách tổng quát.

Ví dụ,

$ git log -p -2 --word-diff
```

![image](https://user-images.githubusercontent.com/69178270/147452708-c368b131-2f57-434b-b974-6c95c405ea2c.png)

```
Để xem thống kê tóm tắt, sử dụng tham số --stat.

Ví dụ,

$ git log --stat
```

![image](https://user-images.githubusercontent.com/69178270/147452781-5fcd0079-9d5d-4e77-9646-534e0dc60099.png)

```
Để xem hiển thị theo nhiều cách khác nhau, sử dụng tham số --pretty.

Ví dụ hiển thị mỗi commit trên một dòng,

$ git log --pretty=oneline
```

![image](https://user-images.githubusercontent.com/69178270/147452893-1816f08c-319b-4a6c-b63a-5b2811c234a8.png)

**Hủy bỏ**

_Hủy bỏ commit cuối cùng_

Chỉnh sửa lại message của lần commit trước, sau khi lưu và đóng lại trình soạn thảo, lệnh commit sẽ được thực thi.

```
$ git commit --amend
```

**Hủy bỏ việc tổ chức một tập tin (unstaging a staged file)**

_Hủy bỏ những thay đổi trên tập tin_

```
$ git checkout -- index.txt
```

**Làm việc với kho chứa ở xa**

 ![image](https://user-images.githubusercontent.com/69178270/147524378-8943f4cc-8163-4525-811f-b89af6d12352.png)

Kho chứa ở xa (remote repository) là 1 hay nhiều phiên bản khác nhau của dự án trên Internet hay trên chính máy tính cá nhân.

