### MySQL - Windows系统下修改basedir路径 :id=title

今天在Windows server 2012上安装了一个MySQL 5.7, 默认安装位置是在`C:\Program Files\MySQL\MySQL Server 5.7`
（如果不是的话，使用下面命令查看）

```text
# 使用cmd进入mysql
mysql -uroot -proot -P3307

mysql> show variables like 'basedir'
```

#### 更改`my.ini`位置

打开服务列表(cmd输入`services.msc`), 找到MySQL, 右键属性可以看到"可执行文件的路径",
我这里的路径是`"C:\Program Files\MySQL\MySQL Server 5.7\bin\mysqld.exe" --defaults-file="C:\ProgramData\MySQL\MySQL Server 5.7\my.ini" MySQL`
,把系统默认的`my.ini`文件复制到数据库的安装目录下。

接下来修改`--defaults-file`的参数，打开注册表(cmd输入`regedit`), 按以下路径查找:

```text
.
└── HKEY_LOCAL_MACHINE
    └── SYSTEM
        └── CurrentControlSet
            └── Services
                └── MySQL
```

在右侧找到`ImagePath`,
将值修改为`"C:\Program Files\MySQL\MySQL Server 5.7\bin\mysqld.exe" --defaults-file="C:\Program Files\MySQL\MySQL Server 5.7\my.ini" MySQL`

到此`my.ini`的位置就修改成功了。

#### 配置`my.ini`, 修改`datadir`

首先将basedir指定的Data文件夹复制到需要更改后的位置，然后打开安装目录下的`my.ini`文件，将basedir的值改为更改后的位置保存即可。

如果改完之后无法启动服务，给Data文件夹添加一个`NETWORK SERVICE`组就可以了，步骤如下：

1. 右键Data文件夹，点击属性。
2. 在顶部Tab选项卡中点击安全。
3. 点击【编辑】按钮，如下图所示：

   ![img.png](img.png)
4. 点击【添加】按钮，输入`NETWORK SERVICE`，然后点击【检查名称】，没有出现错误的话，点击【确定】按钮保存就配置好了。

   ![img_1.png](img_1.png)

   ![img_2.png](img_2.png)
5. 现在启动服务就可以了。
