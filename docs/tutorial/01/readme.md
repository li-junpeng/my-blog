# Windows PowerShell 自定义命令别名

## 前言
在Linux系统上，想要设置命令别名可以在`/home/.bashrc`文件中进行设置，平时Linux系统使用习惯了之后，发现那命令行是真的舒服。同样的功能在Linux和Windows系统上命令还不一样，那么接下来就讲一讲如何在Windows上定义命令别名，将Windows的命令改成Linux命令。

## Linux系统定义别名
1. `vim /home/.bashrc`打开文件
2. 参考以下命令自行设置吧。

```bash
# .bashrc

# User specific aliases and functions

# define git command
alias gp='git pull -i'
alias gs='git status -i'
alias gpush='git push -i'

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi
```

## PowerShell
1. 首先打开一个PowerShell窗口，在命令行中输入`echo $PROFILE`来输出一下PowerShell默认配置文件的路径。

```bash
# 下面是 echo $PROFILE 命令的输出结果
C:\Users\DELL\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```
2. 现在就用编辑工具打开这个文件。
3. 定义别名的规则是以`function`的形式来定义的，格式如下:

```bash
# $args 是参数, 可以接收自定义命令后面的参数信息传递给原始命令
function commandAlias {原命令 $args}
```

4. 现在知道别名定义的规则以后，就可以按照自己的习惯来定义别名啦，以下是我自己定义的一些命令别名，仅供参考:

```bash
function ll {dir $args}
function mv {Rename-Item $args}
function cp {Copy-Item $args}
function rm {Remove-Item $args}

function portstate {netstat -ano | findstr $args}

# git
function gs {git status $args}
function gadd {git add $args}
function gcommit {git commit $args}
function gpush {git push $args}
function gpull {git pull $args}

```
5. 现在只需要重启PowerShell窗口就可以使用刚定义的命令啦~
