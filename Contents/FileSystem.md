# FILE SYSTEM

Linux sử dụng hệ thống tệp phân cấp dưới dạng cây (tree) với một nút gốc (/) là nơi băt đầu của toàn bộ hệ thống hay nút này chứa toàn bộ các file và thư mục của hệ thống.

Dưới đây là cấu trúc file hệ thống trong linux:

<img src="../Images/Linux-File-System.png">

## (/) Root directory
Đây là thư mục gốc của hệ thống, là điểm khởi đầu của toàn bộ hệ thống tệp hay nói cách khác đây là thư mục chứa toàn bộ hệ điều hành của bạn.

## (/bin) binary directory
Đây là thư lục chứa các file thực thi, thường chứa các lệnh terminal, các tiện ích cốt lõi của hệ thông, ví vụ như: `cd` (change directory), `pwd` (print working directory ), `mv` (move) .v.v.

## (/boot) boot directory
Đây là thư mục chứa các file khởi động của hệ thống, với một hệ thông thường sẽ có 4 file:
- `vmlinuz` or `vmlinuz*` là kernel được nén
- `initramfs` là `???` is the initial ram filesystem, required for booting
- `config` là file cấu hình kernel, chỉ sử dụng dể debug
- `system.map` là `???` contains the kernel symbol table, only used for debugging

## (/dev) device directory
Đây là nơi gắn kết các thiết bị, ví dụ như: USB, Ổ đĩa quang, v.v.v

## (/etc) config directory
Đây là thư mục chứa các cấu hình của hệ thống, những file cấu hình ở đây sẽ ảnh hưởng đến toàn bộ người dùng trong hệ thống, ngoài ra người dùng có thể lưu các cấu hình riêng ở thư mục home của người dùng để chỉ ảnh hưởng đến người dùng đó.

## (/home) home directory
Mỗi người dùng trên hệ thống đều có một thư mục riêng của mình và nó nằm ở trong thư mục `/home` thư mục này chứa toàn bộ các thư mục Desktop, Documents, Downloads, Photos và Videos, thư mục này thường có tên trùng với tên người dùng và mõi khi người dùng đăng nhập vào hệ thống thì mặc định sẽ được trỏ đến thư mục này.

## (/lib) library directory
Đây là nơi chứa các thư viện dùng chung, các thư viện được chia sẻ cho các ứng dụng cần đến nó để chạy.

## (/meida) media directory
Là một nơi khác để gắn kết thiết bị như địa CDs, DVDs, USB, .v.v. hệ thống sẽ tự động phát hiện và gắn kết các thiết bị khi được kết nối.

## (/mnt) Mount Directory
Là một thư mục dùng để gắn kết các thiết bị tạm thời khác

## (/opt) Optional directory
Đây là nơi chứa các gói phần phền tùy chọn, nghĩa là các phần mềm chưa được quản lý bới trình quản lý gói.