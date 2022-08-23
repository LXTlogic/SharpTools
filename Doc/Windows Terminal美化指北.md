# Windows Terminal 指北

[TOC]

## 安装 Windows Terminal

> ### 注意
>
> Windows终端需要Windows 10 2004（内部版本19041）或更高版本

### 1. Microsoft Store （推荐）

​ 在 `Microsoft Store` 中搜索 `Windows Terminal` 即可安装。或者从[商店网址](https://aka.ms/terminal)点击跳转安装。

### 2. Github

​ 对于无法从 `Microsoft Store` 安装 `Windows Terminal`的人来说，可以从[Github](https://github.com/microsoft/terminal/releases/latest)下载最新稳定版。

但是这种方法安装的缺点显而易见，不能够自动更新。

### 3. Winget

​ [Winget](https://github.com/microsoft/winget-cli)用户可以通过安装软件包来下载并安装最新的终端版本：`Microsoft.WindowsTerminal`

``` powershell
winget install --id=Microsoft.WindowsTerminal -e
```

​ 除此之外，还有诸如 `Chocolatey` , `Scoop` 等其它安装方式，有此类需求的读者请自行前往 `Windows Terminal` [Github页面](https://github.com/microsoft/terminal#other-install-methods)参考文档安装。

## 设置 Windows Terminal

​ 若诸位想要自定义 `Windows Terminal` 的设置，请在下拉菜单中选择 `设置`。 这将打开设置 UI 以配置设置。

​ 如若想要使用代码来配置 `Windows Terminal` 设置，则可以编辑 settings.json 文件。

> 各版本 `settings.json` 路径：
>
> + **稳定版/通用版：**
>
>     `%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json`
>
> + **预览版：**
>
>     `%LOCALAPPDATA%\Packages\Microsoft.WindowsTerminalPreview_8wekyb3d8bbwe\LocalState\settings.json`
>
> + **未打包版（ `Scoop` 、 `Chocolately` 等）：**
>
>     `%LOCALAPPDATA%\Microsoft\Windows Terminal\settings.json`

​ 当然，这里建议现在UI界面全部设置完后，再使用代码进行配置。此处参数众多，请参考[Windows Terminal Doc](https://docs.microsoft.com/zh-cn/windows/terminal/customize-settings/startup)页面进行配置，如下：

> ## 启动时居中
>
> **属性名称：**`centerOnLaunch`
>
> **接受：**`true`、`false`

---

## Windows Terminal 美化

​ 好吧，这才算是进入了正题😂，本教程将使用[Oh-My-Posh](https://ohmyposh.dev/docs)来进行美化，具体步骤如下：

### 1. 下载 Nerd Fonts

​ 自定义命令提示符通常使用字形（图形符号）来设置提示符的样式。 如果你的字体不包含相应字形，则在整个提示符中，你可能会看到若干 Unicode 替换字符“▯”。 若要在终端中查看所有字形，建议安装 [Nerd Font](https://www.nerdfonts.com/font-downloads)。

可以从提供的字体中挑选一个作为在终端使用的字体，个人建议使用 `Fira Code` 或者 `Jetbrains Mono`作为默认使用字体。

> ### 注意
>
> 在 Vs Code 中，终端字体应该调整为Nerd Font，否则会显示不全。

### 2. 下载及设置 Oh-My-Posh

​ 在此教程中，笔者将使用 Scoop 安装 Oh-My-Posh ，依次执行以下命令：

``` Powershell
scoop install https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/oh-my-posh.json
scoop update oh-my-posh
```

​ 到此，Oh-My-Posh 已将安装到了电脑中，接下来我们需要对其进行设置，以达到美化目的。
