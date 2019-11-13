# SSH-Key

1.[Giới Thiệu](#gioithieu)  
2.[Mô hình lab](#mohinhlab)

2.[Tạo SSH-Key](#create-sshkey)  
3.[Copy SSH-Key](#copy-sshkey)  

<a name="gioithieu"></a>
# Giới Thiệu
SSH-Key là một phương thức xác thực khi ta sử dụng giao thức SSH để truy cập từ xa vào một máy chủ, thay vì sử dụng mật khẩu để xác thực ở đây ta sẽ tạo ra 1 cặp khóa 1 public key và 1 private key, 2 khóa này có sự liên kết với nhau giúp ta có thể xác thực khi ssh vào máy chủ mà không cần đến mật khẩu. 


<a name="mohinhlab"></a>
# Mô hình lab

Ta sẽ có một mô hình lab gồm 2 máy Centos như hình sau:  
<img src="https://github.com/Vy5blkk/Linux/blob/master/Images/sshkey_lab.png">  
Và ta sẽ thực hiện triển khai để máy `CentOS_1` có thể kết nối ssh tới máy `CentOS_2`


<a name="ip-planning"></a>
# Ip-planning
<img src="https://github.com/Vy5blkk/Linux/blob/master/Images/ip-planning.png">

<a name="create-sshkey"></a>
# Tạo SSH-Key
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

### Windows
Đối với windows ta có thể tạo ssh-key bằng một số phần mềm như Putty, MobaXterm hoặc có thể cài git và sử dụng git-bash

<a name="ssh-copy-id"></a>
# Copy ssh-key
Sau khi tạo xong ssh-key ta cần thực hiện copy public key vào máy chủ để có thể tiến hành xác thực bằng ssh-key thay vì mật khẩu

Để copy ssh-key ta thực hiện lệnh sau và thay đường dẫn thư mục người dùng tên người dùng và ip máy chủ hợp lệ:

```
ssh-copy-id -i /home/toor/.ssh/id_rsa.pub root@192.168.235.128
```

Sau khi thực hiện lệnh ta sẽ phải xác thực mật khẩu và public key sẽ được copy tới máy chủ đích, sau đó ta có thể thực hiện ssh vào máy chủ bằng xác thực khóa thay vì mật khẩu

Kết quả:
```
# ssh-copy-id -i /home/toor/.ssh/id_rsa.pub root@192.168.235.128
/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
...
Number of key(s) added: 1

Now try logging into the machine, with:   "ssh 'toor@192.168.235.128'"
and check to make sure that only the key(s) you wanted were added.
```

Sau khi thực hiện một file `authorized_keys` sẽ được tạo ra trong thư mục `.ssh` trên máy chủ, đó chính là public key mà ta vừa thực hiện copy

Cuối cùng ta chỉ cần ssh vào máy chủ và việc xác thực sẽ được thực hiện bằng khóa ssh.