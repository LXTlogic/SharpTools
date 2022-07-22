# Scoop 安装配置指北

- [Scoop 安装配置指北](#scoop-安装配置指北)
  - [前言](#前言)
    - [配置要求](#配置要求)
  - [安装Scoop](#安装scoop)
    - [1. 自定义安装路径（不需要的可以跳过）](#1-自定义安装路径不需要的可以跳过)
    - [2.安装](#2安装)
    - [3. 高级安装（官网推荐）](#3-高级安装官网推荐)
  - [Scoop使用](#scoop使用)
    - [1. 基本使用](#1-基本使用)
    - [2. 软件安装及卸载](#2-软件安装及卸载)
    - [3. 软件更新](#3-软件更新)
    - [4. 添加bucket](#4-添加bucket)
    - [5. 软件推荐](#5-软件推荐)
    - [6. 其它问题](#6-其它问题)
  - [参考链接](#参考链接)

## 前言

Scoop 是一个 Win­dows 包管理工具，类似于 De­bian 的 `apt`、ma­cOS 的`homebrew`。

Scoop主要优点有：

+ 开源
+ 消除权限弹出窗口
+ 隐藏具有GUI引导的安装程序
+ 避免大量应用程序污染环境变量（所有安装软件均在一个指定目录）
+ 自动查找并安装依赖项
+ 自行执行所有额外的设置步骤以获取所需程序

### 配置要求

+ Windows 7 SP1+ / Windows Server 2008+

+ `PowerShell 5.1` （或更高版本，包括 `PowerShell Core` ）和 `.NET Framework 4.5`（或更高版本）；

    ```powershell
    $PSVersionTable.PSVersion.Major  # 查看Powershell版本
    $PSVersionTable.CLRVersion.Major  # 查看.NET Framework版本
    ```

+ Windows 用户名为英文；

+ 正常、快速的访问GitHub并下载资源。

---

## 安装Scoop

Scoop 默认使用普通用户权限，其本体和安装的软件默认会放在  `%USERPROFILE%\scoop`(即 `C:\Users\用户名\scoop` )，使用管理员权限进行全局安装 ( `-g` ) 的软件在 `C:\ProgramData\scoop`。如果有自定安装路径的需求，需要提前设置好环境变量。

### 1. 自定义安装路径（不需要的可以跳过）

Scoop默认安装位置是 `C:\Users\scoop` 当然，你也可以通过Windows的系统属性→高级→环境变量中设置以下内容

打开 `PowerShell`,
+ 设置用户安装路径，以 `D:\Scoop` 为例：
    ``` powershell
    $env:SCOOP='D:\Scoop'
    [Environment]::SetEnvironmentVariable('SCOOP', $env:SCOOP, 'User')
    ```

+ 设置全局安装路径（需要管理员权限），以 `D:\GlobalScoop`  为例：
    ``` powershell
    $env:SCOOP_GLOBAL='D:\GlobalScoop'
    [Environment]::SetEnvironmentVariable('SCOOP_GLOBAL', $env:SCOOP_GLOBAL, 'Machine')
    ```

### 2.安装

1. 允许PowerShell执行远程脚本，如果已经设置过了可以忽略。

    ``` Powershell
    Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
    ```

​	出现提示 `是否要更改执行策略?` ，输入 Y 或 A 回车。

2. 安装Scoop

    ``` PowerShell
    iwr -useb get.scoop.sh | iex
    ```

​	如果下载Scoop的过程中断，那么必须先删除Scoop安装文件夹，再执行以上命令安装。

### 3. 高级安装（官网推荐）

下载Scoop安装程序并使用参数手动执行。

``` powershell
irm get.scoop.sh -outfile 'install.ps1'		#install.ps1文件默认在终端程序当前所在目录
```

查看安装程序所有的配置参数

``` powershell
.\install.ps1 -?
```

例如，将Scoop安装到自定义目录，将Scoop全局程序配置为自定义目录，并在安装时绕过系统代理：

``` powershell
.\install.ps1 -ScoopDir 'D:\Applications\Scoop' -ScoopGlobalDir 'F:\GlobalScoopApps' -NoProxy
```

---

## Scoop使用

### 1. 基本使用

+ 寻找软件：`scoop search app_name`
+ 软件介绍：`scoop info app_name`
+ 安装软件：`scoop install app_name`
+ 卸载软件： `scoop uninstall app_name`
+ 已安装软件列表：`scoop list`
+ 查看软件状态：`scoop status`
+ 清理安装包：`scoop cache rm app_name` 或者 `scoop cache rm *`
+ 查看可添加仓库：`scoop bucket known`
+ 添加额外仓库：`scoop bucket add 仓库名`



### 2. 软件安装及卸载

```powershell
scoop install aria2		#安装Aria2，达到加速下载的目的
scoop config aria2-max-connection-per-server 16		#设置Aria2连接数为16
scoop config aria2-min-split-size 4M		#Aria2下载文件分块的大小
scoop config aria2-enabled false		#在使用代理软件时，Aria2经常会出错，可以使用这行命令关闭Aria2

scoop install 7zip		#安装7zip，很多软件需要它才能安装
scoop install git		#安装git，Scoop的bucket本质上都是一个git库，所以想要添加额外的存储库，需要有git环境支撑

scoop install -g app_name		#如果想要全局安装，以管理员身份打开PowerShell
scoop install -g sudo		#或者可以安装sudo，然后在普通身份时也可以对全局进行操作。注意：此时以管理员身份打开Powershell
```

```powershell
scoop unistall app_name		#卸载软件

scoop cleanup app_name		#清除某一软件旧版本安装信息
scoop cleanup *		#清除所有软件旧版本安装信息
```



### 3. 软件更新

```powershell
scoop update app_name		#指定更新软件
scoop update *		#更新全部软件
scoop update		#更新Scoop以及全部bucket

scoop hold app_name		#停止更新某一软件
```



### 4. 添加bucket

​	bucket可以理解为一个软件库，里面有很多的软件来源。

```powershell
scoop bucket known		#列出官方认可的bucket
----------------------------------------------------------------
main		#默认bucket
extras
versions		#一些软件的旧版本
nirsoft		#NirSoft开发的小工具的合集，包括系统工具、网络工具、密码恢等
php
nerd-fonts
nonportable
java		#java JDK
games
```

```powershell
scoop bucket add extras		#一般来说，添加extras已经够用了

scoop bucket rm bucket_name		#删除某个bucket
```

### 5. 软件推荐

+ Scoop-Completion

    ```powershell
    scoop bucket add extras		#添加bucket
    scoop install scoop-completion		#安装scoop-comletion
    Import-Module "$($(Get-Item $(Get-Command scoop.ps1).Path).Directory.   Parent.FullName)\modules\scoop-completion"		#在当前终端启用自动补全

    notepad $profile		#如需要自动启动自动补全，需要配置配置文件，将上一行 “Import……”添加到配置文件中。
    scoop uninstall scoop-completion		#如果设置了自动启动，卸载后需要将   $profile 中的启用代码删除
    ```



### 6. 其它问题

``` powershell
scoop help		#查看命令列表及帮助
scoop help <commmand>		#查看有关特定命令帮助
scoop config proxy 127.0.0.1:4412		#设置代理
scoop config rm proxy		#移除代理
scoop checkup		#安装各种包时或者进行了一些配置时，可能会造成一些冲或错误，可以使用该命令检查，并按照提示来解决。
scoop reset app_name		#重置某一软件，或者实现版本切换
scoop reset *		#重置全部软件
```

## 参考链接

1. [ScoopInstaller/Install](https://github.com/ScoopInstaller/Install)

2. [ScoopInstaller/Scoop](https://github.com/ScoopInstaller/Scoop)
3. [~/Scoop](https://scoop.netlify.app/)