# SSH-Key

1.[Giới Thiệu](#gioithieu)  
2.[Tạo SSH-Key](#create-sshkey)  
3.[Copy SSH-Key](#copy-sshkey)  

<a name="gioithieu"></a>
# Giới Thiệu


<a name="create-sshkey"></a>
# Tạo SSH-Key
### Windows
### Linux
Để tạo ssh-key trên linux ta sử dụng lệnh
```
ssh-keygen -t rsa -b 4096
```
với:  
`-t` chỉ định loại mã hóa được sử dụng, ở đây là rsa  
`-b` chỉ định độ dài khóa  
Sau khi thực hiện lệnh sẽ tạo ra 1 cặp khóa, 1 public key và 1 private key ở thư mục `~\.ssh\` nêu không được chỉ định đường dẫn

```
[toor@CentOS-7 ~]$ ssh-keygen -t rsa -b 4096
Generating public/private rsa key pair.
Enter file in which to save the key (/home/toor/.ssh/id_rsa):
Created directory '/home/toor/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/toor/.ssh/id_rsa.
Your public key has been saved in /home/toor/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:tY3UuzbQE/ivYaypKr8CDf5RzfdgfKus+lyZPM7W0fI toor@CentOS-7
The key's randomart image is:
+---[RSA 4096]----+
|                 |
|           o     |
|       o .+ o    |
|  .   . oo=*.o   |
| . o .  So++*o   |
|  o o    . ==+.  |
|   o .   .*oB+.  |
|    +  . ++*.+E  |
|     +===+= .    |
+----[SHA256]-----+
[toor@CentOS-7 ~]$
```

<a name="ssh-copy-id"></a>
# Copy ssh-key
Sau khi tạo xong ssh-key ta cần thực hiện copy public key vào máy chủ để có thể tiến hành xác thực bằng ssh-key thay vì mật khẩu

Để copy ssh-key ta thực hiện lệnh sau và thay đường dẫn thư mục người dùng tên người dùng và ip máy chủ hợp lệ:

```
ssh-copy-id -i /home/toor/.ssh/id_rsa.pub root@192.168.235.128
```

Sau khi thực hiện lệnh 
