# Working with files

Cấu trúc file và thư mục trên linux được tổ chức theo dạng cây thư mục bắt đầu từ thư mục gôc (`/`).

Trong linux, hệ thống tệp được chia làm 3 loại:
- File thông thường
- Thư mục
- File đặc biệt

Khi ta liệt kê file sẽ có kết quả tương tự như sau:
```
[toor@CentOS-7 /]$ ls -la /
total 20
dr-xr-xr-x.  17 root root  224 Nov 11 22:07 .
dr-xr-xr-x.  17 root root  224 Nov 11 22:07 ..
lrwxrwxrwx.   1 root root    7 Nov 11 21:59 bin -> usr/bin
dr-xr-xr-x.   5 root root 4096 Nov 11 22:08 boot
drwxr-xr-x.  20 root root 3200 Nov 13 02:31 dev
drwxr-xr-x.  74 root root 8192 Nov 13 02:31 etc
drwxr-xr-x.   3 root root   18 Nov 11 22:07 home
lrwxrwxrwx.   1 root root    7 Nov 11 21:59 lib -> usr/lib
lrwxrwxrwx.   1 root root    9 Nov 11 21:59 lib64 -> usr/lib64
drwxr-xr-x.   2 root root    6 Apr 11  2018 media
drwxr-xr-x.   2 root root    6 Apr 11  2018 mnt
drwxr-xr-x.   2 root root    6 Apr 11  2018 opt
dr-xr-xr-x. 110 root root    0 Nov 13 02:31 proc
dr-xr-x---.   2 root root  135 Nov 13 01:50 root
drwxr-xr-x.  23 root root  720 Nov 13 02:31 run
lrwxrwxrwx.   1 root root    8 Nov 11 21:59 sbin -> usr/sbin
drwxr-xr-x.   2 root root    6 Apr 11  2018 srv
dr-xr-xr-x.  13 root root    0 Nov 13 02:31 sys
drwxrwxrwt.  11 root root 4096 Nov 13 02:32 tmp
drwxr-xr-x.  13 root root  155 Nov 11 21:59 usr
drwxr-xr-x.  19 root root  267 Nov 11 22:13 var
[toor@CentOS-7 /]$

```
Trong đó:
- Cột đầu tiên thể hiện loại tệp và quyền (permission)
- Cột thư hai thể hiện bộ nhớ
- Cột thứ ba thể hiện quyền sở hữu
- Cột Thứ tư thể hiện nhóm sở hữu
- Cột thứ năm thể hiện kích thước tệp tính theo byte
- Cột thư sau thể hiện thời gian tạo hoặc cập nhật lần cuối
- Cột cuối cùng là tên của file hoặc thư mục

## Quyền truy cập file và thư mục

Trong linux quyền được chia thành 3 nhóm khác nhau:

|#|Description|
|-|-----------|
|owners|Chủ sở hữu, là người sở hữu tệp|
|group|Là nhóm sở hữu|
|Others|Là những nhóm người dùng khác|