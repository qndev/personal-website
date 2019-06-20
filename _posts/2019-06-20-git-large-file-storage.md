---
title: "Git Large File Storage"
published: true
comments: true
---

## Bắt đầu với LFS ##

### Yêu cầu ###

#### :small_red_triangle: `git >= 1.8.2` ####

### Cài đặt ###

#### :pushpin: Debian ###

:small_red_triangle: Cấu hình trước khi cài đặt.

:small_orange_diamond: Refresh lại các packages trong bộ nhớ đệm bằng cách.

```bash
$ sudo apt-get update
```

:small_orange_diamond: Nếu bạn đang sử dụng hệ điều hành Debian cần cài đặt `debian-archive-keyring` để xác thực các repositories của Debian.

```bash
$ sudo apt-get install debian-archive-keyring
```

:small_orange_diamond: Ngoài ra cũng yêu cầu một số tools cần được cài đặt trước khi aifcaif đặt Git LFS.

```bash
$ sudo apt-get install curl gnupg apt-transport-https
```

:small_orange_diamond: Cài đặt [GPG key](https://packagecloud.io/docs#gpg) bằng cách sử dụng [apt-key](http://man.he.net/man8/apt-key).

```bash
$ curl -L https://packagecloud.io/github/git-lfs/gpgkey | sudo apt-key add -
```

:small_orange_diamond: Cấu hình kho chứa repository bằng cách tạo file `/etc/apt/sources.list.d/github_git-lfs.list`  và chứa thông tin packagecloud repo đưới đây với hai option [Linux distribution version](https://packagecloud.io/docs#os_distro_version) là **`os`** và **`dist`**.

```bash
$ deb https://packagecloud.io/github/git-lfs/debian/ stretch main
$ deb-src https://packagecloud.io/github/git-lfs/debian/ stretch main
```
:small_orange_diamond: Refresh

```bash
$ sudo apt-get update
```
:small_red_triangle: Cài đặt.

```bash
$ curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash
$ sudo apt-get install git-lfs
$ git lfs install
```

#### :pushpin: Mac OSX ###

```bash
$ brew update
$ brew install git-lfs
$ git lfs install
```

#### :pushpin: Ubuntu ###

:small_orange_diamond: **```$ curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash```**

:small_orange_diamond: **```$ sudo apt-get install git-lfs```**

:small_orange_diamond: **```$ git lfs install```**

#### :pushpin: Windows ###

:small_orange_diamond: Download [Windows installer](https://github.com/git-lfs/git-lfs/releases)

:small_orange_diamond: Chạy Windows installer vừa download về

:small_orange_diamond: Mở command prompt và chạy _`git lfs install`_

## Sử dụng Git LFS ##

:small_orange_diamond: Để bắt đầu sử dụng Git LFS trong Git repository chưa được cấu hình cho Git LFS, bạn có thể chỉ ra tệp nào bạn muốn Git LFS quản lý.

```bash
$ git lfs track "*.iso"
```

:small_orange_diamond: Ở đây git-lfs sẽ track tất cả các file có dạng _`*.iso`_. Để xem danh sách các file có dạng _`*.typeoffile`_ tracked bởi git-lfs, chỉ cần chạy _`git lfs track`_. Để hiển thị tất cả các file đã tracked sau khi commit: _`git lfs ls-files`_.

:small_orange_diamond: Tiếp theo cần add file [.gitattributes](https://git-scm.com/docs/gitattributes) vào git repo bởi vì _`git lfs track`_ lưu trữ khuôn mẫu, file dạng `*.typeoffile` trong _`.gitattributes`_.

```bash
$ git add .gitattributes
$ git commit -m "track *.iso files sử dụng Git LFS"
```

:small_orange_diamond: Bây giờ chúng ta có thể thao tác với Git repository như bình thường, và Git LFS sẽ quản lý những files có kichs thước lớn có trong định dạng _`.gitattributes`_. Ví dụ add file myfile.iso.

```bash
$ git add myfile.iso
$ git commit -m "add myfile.iso"
```

> _Note:_ Nếu files đã có trong history của repository , `git lfs
> track` sẽ _không_ quản lý chúng (track). Để làm được diều đó
> cần sử dụng `git lfs migrate`. Ví dụ:
>
> ```
> $ git lfs migrate import --include="*.iso"
> ```
> [git-lfs-migrate(1)](https://github.com/git-lfs/git-lfs/blob/master/docs/man/git-lfs-migrate.1.ronn).

:small_orange_diamond: Để xác định xem file _`iso`_ vừa commit đã được Git LFS quản lý hay chưa bằng cách:

```bash
$ git lfs ls-files
8c15b8b603 * myfile.iso
```

:small_orange_diamond: Cuối cùng push files lên Git remote:

```bash
$ git push origin master
```
