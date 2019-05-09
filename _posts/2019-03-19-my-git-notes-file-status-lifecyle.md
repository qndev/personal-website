---
title: "My git notes - File Status LifeCyle"
published: true
---

### Một số câu lệnh cơ bản thông qua trạng thái của file/tập tin trong repository

<img src="{{ '/assets/images/gitstatus.png' | absolute_url }}" alt="File Status LifeCyle">

* #### Giả sử ta đang làm việc tại thư mục /home/quangnd.

Tạo thư mục làm việc của dự án với câu lệnh: mkdir < tên thư mục >.

```console
VD:
     * mkdir git
     * Tiếp theo di chuyển vào thư mục git vừa tạo: cd git
     * Khởi tạo repository: git init.
     * Hiển thị thông tin về repository vừa tạo: git status
```

```console
On branch master

    Initial commit

    nothing to commit (create/copy files and use "git add" to track)
```

* #### Lúc này ta thấy được trong repository chưa có gì thay đổi, trong thư mục khu vực làm việc chưa có bất kì file hay tập tin gì do vậy trạng thái lúc này là untracked.


* #### Tiếp theo ta có thể thêm mới một file tên là git-repository trong thư mục git vừa tạo. (với lệnh touch git-repository)

* #### Tiếp tục kiểm tra trạng thái repository: git status

```console
On branch master

    Initial commit

    Untracked files:
     (use "git add <file>..." to include in what will be committed)

    git-repository

    nothing added to commit but untracked files present (use "git add" to track)
```

* #### Lúc này ta đã thêm mới một file git-repository vào trong thư mục git và trạng thái của nó vẫn đang là untracked và output commandline có gợi ý câu lệnh git add < file >.

* #### Thực hiện lệnh git add git-repository lúc này file git-repository vẫn đang ở trạng thái untracked do git-repository mới thêm lần đầu và chưa có bất kì commit nào lên repository.

* #### Bây giờ thêm mới nội dung bất kỳ trong file git-repository và lưu lại. Kiểm tra trạng thái một lần nữa ta sẽ thấy:

```console

On branch master

Initial commit

Changes to be committed:
(use "git rm --cached <file>..." to unstage)

 new file: git-repository

Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git checkout -- <file>..." to discard changes in working directory)

modified: git-repository

```

* #### File git-repository bây giờ đã thay đổi trạng thái trở thành modified và có thể add để cập nhật nội dung chuẩn bị cho commit đầu tiên (git add git-repository).

* #### Sau khi add file tiếp tục lại thay đổi trạng thái: thành staged.

* #### Cuối cùng commit file: git commit -m “first commit”

* #### Kiểm tra lại trạng thái các tệp tin và thấy chúng lại trở về trạng thái unmodified.

* #### Ngoài ra để xem sự thay đổi của các tệp tin ta sử dụng lệnh git diff để xem nột dung các thay đổi của file khi nó ở trạng thái unstaged hay chỉ modified.

* #### Hoặc git diff --cached (--staged option tương tự như --cached)để xem những thay đổi đã staged chuẩn bị commit.

* #### Thay đổi tên tập tin với lệnh git mv < tên file hiện tại > < tên file muốn thay đổi >.

* #### Một trường hợp nữa đặt ra đó là bạn commit quá sớm mà sau khi commit bạn mới nhận ra vẫn còn một số file còn thiếu trong lần commit đó và bạn không muốn commit mới mà vẫn sử dụng commit với thông điệp cũ cùng commit hoặc thay đổi message đó có thể sử dụng git commit –amend.

* #### Một số lệnh commit cơ bản khác:

```console
git checkout -- <file name> # Loại bỏ các thay đổi trước đó.
git reset HEAD <file name> # Loại bỏ tập tin ra khỏi khu vực staging area.
```
