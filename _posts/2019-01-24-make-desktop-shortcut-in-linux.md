---
title: "Tạo desktop shortcut application trong linux"
published: true
comments: true
---

Khi cài đặt các ứng dụng trên các hệ điều hành nhân Linux có rất công cụ để xử lý việc này. Tuy nhiên có những ứng dụng đã có sẵn các gói đã được biên dịch sẵn, chứa các file thực thi đã được build từ trước. Khi muốn chạy hoặc khởi tạo ứng dụng lần đầu chúng ta thường tìm đến file setup có đuôi .sh, cấp quyền thực thi cho nó. Để làm được như vậy cần thực hiện một số câu lệnh:

```bash
$ sudo chmod + x <file-setup-name>.sh
$ ./<file-setup-name>.sh
```

Vậy trong các binary package đó thì biết được đâu là file setup cần chạy:  thông thường khi download tool nào đó về và giải nén nó ra thường có file README có thông tin về tác giả, các setup,... có thể cho chúng ta biết được thông tin cài đặt.

Như vậy cứ mỗi lần chạy ứng dụng ta lại truy cập vào thư mục <file-setup-name>.sh để thực thi bash script <kbd>./file-setup-name.sh </kbd> thực sự không thuận tiện cho lắm.

Để giải quyết vấn đề này ta có thể tạo shortcut thay thế:

- Tạo file shortcut với định dạng <file-shortcut-name>.desktop (chú ý viết liền hoặc có gạch nối giữa các từ).

```bash
$ touch <file-shortcut-name>.desktop
```

- Edit file shortcut vừa tạo với nội dung:

```bash
[Desktop Entry]
         Name=Tên ứng dụng
         Comment=Comment
         Exec=/Đường dẫn đến file <file-setup-name>.sh
         Path=/Đường dẫn đến thư mục chứa file <file-setup-name>.sh
         Icon=/Đường dẫn đến file icon hiển thị cho ứng dụng/
         Categories=Application;Development;Java;IDE;Android
         Version=1.0
         Type=Application
         Terminal=false
```

- Ví dụ edit thông qua nano text editor commandline (đơn giản hơn bạn có thể mở file <file-shortcut-name>.desktop bằng gedit text editor GUI)

```bash
$ nano android-studio.desktop
```

- Cấp quyền thực thi file <file-shortcut-name>.desktop.

```bash
$ sudo chmod +x <file-shortcut-name>.desktop
```
- Sao chép file vào thư mục chứa các ứng dụng chương trình của bạn.

```bash
$ sudo cp <file-shortcut-name>.desktop /usr/share/applications/
```
Ví dụ: Tạo shortcut cho IDE Android Studio.

```bash
[Desktop Entry]
         Name=Android Studio
         Comment=Android Studio
         Exec=/home/quangnd/android-studio/bin/studio.sh
         Path=/home/quangnd/android-studio/bin/
         Icon=/home/quangnd/android-studio/bin/studio.png
         Categories=Application;Development;Android;IDE;Java
         Version=1.0
         Type=Application
         Terminal=false
```

  <img src="{{ '/assets/images/desktop-shortcut.png' | absolute_url }}" alt="" height="495px" width="700px">
