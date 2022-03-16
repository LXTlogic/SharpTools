# Scoop 安装配置指北

## 前言

Scoop 是一个 Win­dows 包管理工具，类似于 De­bian 的 `apt`、ma­cOS 的`homebrew`。

Scoop主要优点有：

+ 开源
+ 消除权限弹出窗口
+ 隐藏具有GUI引导的安装程序
+ 避免大量应用程序污染环境变量（所有安装软件均在一个指定目录）
+ 自动查找和安装依赖项
+ 自行执行所有额外的设置步骤以获取所需程序

## 配置要求

+ Windows 7 SP1+ / Windows Server 2008+
+ `PowerShell 5` （或更高版本，包括 `PowerShell Core` ）和 `.NET Framework 4.5`（或更高版本）；
+ Windows 用户名为英文；
+ 正常、快速的访问 `GitHub` 并下载资源。

## 安装Scoop

Scoop 默认使用普通用户权限，其本体和安装的软件默认会放在  `%USERPROFILE%\scoop`(即 `C:\Users\用户名\scoop` )，使用管理员权限进行全局安装 ( `-g` ) 的软件在 `C:\ProgramData\scoop`。如果有自定安装路径的需求，那么要提前设置好环境变量。

### 1. 自定义安装路径（不需要的可以跳过）

当然，你也可以通过Windows的系统属性→高级→环境变量中设置以下内容

打开 `PowerShell`,
+ 设置用户安装路径
    ``` powershell

        $env:SCOOP='你想把应用安装到的位置'
        [Environment]::SetEnvironmentVariable('SCOOP', $env:SCOOP, 'User')
    ```

+ 设置全局安装路径（需要管理员权限）
    ``` powershell

        $env:SCOOP_GLOBAL='你想把全局应用安装到的位置'
        [Environment]::SetEnvironmentVariable('SCOOP_GLOBAL', $env:SCOOP_GLOBAL, 'Machine')

    ```

### 2.开始

1. 允许PowerShell执行本地脚本

``` Powershell

    Set-ExecutionPolicy RemoteSigned -scope CurrentUser

```

2. 安装Scoop

``` PowerShell

    Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')

    # 或者
    iwr -useb get.scoop.sh | iex

```