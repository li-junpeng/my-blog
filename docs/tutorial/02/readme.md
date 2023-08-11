# Linux 配置私钥登录

## 1. 生成密钥对

```bash
[root@junpeng ~]# ssh-keygen -t rsa
Generating public/private rsa key pair.
Enter file in which to save the key (~/.ssh/id_rsa): 
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in ~/.ssh/id_rsa
Your public key has been saved in ~/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:ld05caohZqodw3m+FMJK1J2aYkI6MU4wP8cEEWB5Pp8 junpeng@Junpeng-Pc
The key's randomart image is:
+---[RSA 3072]----+
|+o=+.         . .|
|.= +   . . + . = |
|  O + . . O o =  |
| o X . o O . o . |
|  + + = S o .    |
|   . E = * .     |
|      o . o      |
|         . .     |
|          .      |
+----[SHA256]-----+
```

在`/root/.ssh`目录下会生成两个文件，一个是`id_rsa`私钥，一个是`id_rsa.pub`公钥
## 2. 安装公钥

```bash
[root@junpeng ~]# cd /root/.ssh
[root@junpeng .ssh]# ls
id_rsa    id_rsa.pub
[root@junpeng .ssh]# cat id_rsa.pub >> authorized_keys
[root@junpeng .ssh]# chmod 600 authorized_keys
[root@junpeng .ssh]# chmod 777 ~/.ssh
```

## 3. 验证
使用SSH工具连接服务器，连接参数选择私钥连接，然后将`id_rsa`文件的内容输入就可以正常连接啦。
