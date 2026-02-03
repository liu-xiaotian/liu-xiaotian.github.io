+++
date = '2026-02-03T23:00:58+08:00'
draft = true
title = 'Git Bash配置Zsh'

+++

# Windows安装 Zsh 终端

- - -

## 前言

本文以 `Git Bash` 终端为基础，来安装 `Zsh`终端和 `powerlevel10k` 主题，轻松易上手。

本文以 `Windows Terminal` 为例，也就是 `Windows 11` 中的 `终端`，`Windows 10` 没有的话，可以去应用商店搜索并下载。但这并不是必须的，你使用 `Git Bash` 也是可以的。

## 安装 git bash

下载 \[windows版本git]，一般来说，下载64位版本：

![](https://blog.xlxs.top/upload/2024/09/755c96a48abb4f969a401886964aa879tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

在安装的过程中，记得勾选 `Add a Git Bash Profile to Windows Terminal` （如果你不习惯使用window终端，喜欢使用 `Git Bash`，那么下面这几步可以跳过），之后的安装一直下一步即可：

![](https://blog.xlxs.top/upload/2024/09/41c997181ca94ed6b22c6b7ed0c259actplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

勾选是为了在 `Windows Terminal（终端）` 中能够使用 `Git Bash`，可以看一下，原本终端是没有 `Bit Bash` 选项的：

![](https://blog.xlxs.top/upload/2024/09/2131f59403894200b02fe81ef3a9d598tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

安装 `git` 之后，重新打开终端，在标签页选择项中就可以看到 `Git Bash` 的选择项了：

![](https://blog.xlxs.top/upload/2024/09/54086d16767a4188ad2fbd9bc0190e41tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

> 如果在安装 `Git` 的时候勾选了这个选项，但是没有出现 `Git Bash` 选项的话，可能是 `Windows Terminal` 版本过低，在应用商店中搜索 `Windows Terminal`，更新一下即可。

## 安装 zsh

下载 [zsh安装包](https://packages.msys2.org/packages/zsh?repo=msys\&variant=x86_64)：

![](https://blog.xlxs.top/upload/2024/09/3b4d8bea9954432fadcc4bba84650d52tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

将 zsh 安装包解压到 git 的安装根目录下，可以使用 [7-Zip-zstd](https://github.com/mcmilk/7-Zip-zstd/releases) 解压：

![](https://blog.xlxs.top/upload/2024/09/ff05eac9b7dd4313ad9e383be0ba045ctplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

需要解压两次，第一次解压，解压到当前目录即可，得到 `.tar`文件：

![](https://blog.xlxs.top/upload/2024/09/424b68580b174d0484f1813ac9488efbtplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

第二次解压 `.tar`文件到当前目录（直接解压到 git 安装目录可能会没有权限）：

![](https://blog.xlxs.top/upload/2024/09/993c9ca6db6c49a59f474062788aa21dtplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

移动解压后的文件到 `git` 安装目录即可，需要权限的话就授权，重名的话直接覆盖：

![](https://blog.xlxs.top/upload/2024/09/196d05cbbe83497bb0aaf8fc03068fe4tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

打开 `Git Bash` 标签页或者直接右键打开 `Git bash` 输入 `zsh`，出现下图则安装成功：

![](https://blog.xlxs.top/upload/2024/09/44eb70470a944d9498fa8d175d88dee9tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

暂时先不进行其他设置，直接输入 `0` 结束并生成 `.zshrc` 配置文件即可。

由于现在没有安装 `zsh` 主题，可以这样区分 `bash` 和 `zsh`，`bash`的光标在第二行，`zsh`的光标在同一行：

![](https://blog.xlxs.top/upload/2024/09/92f0ab0049674ced9dc79b40a164f84dtplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

## 设置默认启动

### 设置 Git Bash 默认使用 Zsh

每次打开 `Git Bash` 终端，你会发现默认还是 `Bash` 终端，而不是 `Zsh`，可以通过编辑 `Bash` 终端的配置文件 `.bashrc` 来实现默认使用 `Zsh`，在 `Git Bash` 终端中输入命令：

shell

____

```shell
01
vim ~/.bashrc
```

![](https://blog.xlxs.top/upload/2024/09/af4706a78199455884b140f2ea921f1atplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

`Vim` 默认是命令模式，你可以直接将配置内容粘贴进去，然后输入冒号 `:` 进入尾行模式，在尾行模式输入小写 `wq` 最后按回车键，保存退出：

shell

____

```shell
010203
if [ -t 1 ]; then
  exec zsh
fi
```

![](https://blog.xlxs.top/upload/2024/09/a8969499f9a046ed9e40f9dfe517db3btplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

> 也可以在 vim 命令模式按小写 `i` 进入插入模式，之后粘贴或写入内容，按 `Esc` 退出插入模式，然后输入冒号 `:` 进入尾行模式，在尾行模式输入小写 `wq` 最后按回车键，保存退出

之后再打开 `Git Bash` 终端，默认就会使用 `Zsh` 了。第一次可能有一个警告：大概是找不到 `~/bash_profile` 等一些文件，可以忽略，以后不会再出现了。

### 设置 Windows Terminal 默认使用 Git Bash

每次打开 `Windows Terminal` 默认使用的是 `Windows PowerShell`，要改为默认使用 `Git Bash`，在设置里面进行设置即可。在更多选项中点击设置，或者右键标题栏空白处再点击设置，设置 `Git Bash` 为默认终端：

![](https://blog.xlxs.top/upload/2024/09/96bcb7b343294f2bb941d03d581b419btplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

## 安装 Oh My Zsh

在安装好 `Zsh` 终端之后，看起来跟 `Bash` 终端并无太大的区别，我们也没有进行设置。而 `Oh My Zsh` 可以用于管理 `Zsh`配置。它捆绑了数千个有用的功能、助手、插件、主题等。

在命令行输入命令并按回车执行：

shell

____

```shell
01
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

出现下图的内容就是安装成功了，如果出现错误，或长时间没有响应，多试几次即可：

![](https://blog.xlxs.top/upload/2024/09/236e82f094d8429e8a29e50a9284cc42tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

> 最后一行的 `ERROR` 可以忽略

## 配置 zsh

`Zsh`的配置文件在用户的家目录，文件是 `.zshrc`，编辑配置文件，可以对 `Zsh`进行一些定制化配置：

shell

____

```shell
01
vim ~/.zshrc
```

编辑并保存配置文件之后，并不会立即生效，可以关闭所有终端重新打开，或者使用命令让配置生效：

shell

____

```shell
01
source ~/.zshrc
```

### 配置主题

`Oh My Zsh` 安装默之后，默认使用主题是 `robbyrussell`，可以修改 `.zshrc` 配置中的 `ZSH_THEME` 字段，所有可用主题可参考[ohmyzsh官方文档](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes)，这里先配置一下我个人比较喜欢的主题：

![](https://blog.xlxs.top/upload/2024/09/5d94752c1a1944269498015d045c6476tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

### 配置插件

通过使用插件，可以让 `Zsh` 的功能更加强大，`Zsh` 和 `Oh My Zsh` 自带了一些实用的插件，也可以下载其他的插件。 如 `Zsh` 自带 `Git` 插件，可以在命令行显示 `Git` 相关的信息，并提供了一些操作 `Git` 的别名：

shell

____

```shell
0102030405
gaa = git add --all
gcmsg = git commit -m
ga = git add
gst = git status
gp = git push
```

![](https://blog.xlxs.top/upload/2024/09/ac0d10e9f0c04bd58fc465208f94f836tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

#### 自动补全

`zsh-autosuggestions` 插件，可以在你历史指令中找到与你当前输入指令匹配的记录，并高亮显示，如果想直接使用，可以直接通过右方向键补全。 安装插件，在终端分别执行下面两条命令：

shell

____

```shell
010203
cd ~/.oh-my-zsh/custom/plugins

git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

插件下载完成之后，编辑 `~/.zshrc` 配置文件，修改插件相关配置项：

shell

____

```shell
01
vim ~/.zshrc
```

![](https://blog.xlxs.top/upload/2024/09/8499339231914a5ca2d9bb1e912b5ca6tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

保存退出之后，记得使用命令 `source ~/.zshrc` 重载配置。该插件生效之后，在使用命令的时候，就会匹配我们使用的命令，右键可以直接补全：

![](https://blog.xlxs.top/upload/2024/09/79f24e2aef744d9586db8d414c3f083ctplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

如果你不喜欢提示默认的浅灰色，可以在 `~/.zshrc` 中修改（没有配置项就添加），更多配置可以参考[zsh-autosuggestions官方文档](https://github.com/zsh-users/zsh-autosuggestions#suggestion-highlight-style)：

shell

____

```shell
01
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE="fg=#9fc5e8"
```

#### 目录跳转

`Zsh` 自带有一个插件 `z`，可以让我们在访问过的目录中快速跳转，将该插件配置到 `~/.zshrc` 文件中即可使用：

![](https://blog.xlxs.top/upload/2024/09/e2f765e52e5e4db08cf8becf00410743tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

保存退出之后，重载配置，随意进入一些目录，之后再使用命令 `z` 就可以实现快速跳转，支持模糊匹配：

![](https://blog.xlxs.top/upload/2024/09/6202e7af4e2f46a4b9050f7e964c9351tplv-k3u1fbpfcp-zoom-in-crop-mark1512000.webp)

或许相比于 `z`，更多人会选择使用 `autojump`，如果是 `Mac` 或者 `Linux` 没什么问题，`Windows` 就不太建议折腾了。

## 设置 IDEA、Studio 默认使用 Zsh

1. 打开 VS Code 设置 （File -> Preferences -> Settings）
2. 搜索 `terminal.integrated.profiles.windows` ，点击在 settings.json 中编辑
3. 添加以下配置（路径根据你的 Git 实际安装位置修改，通常默认路径如下）：

~~~
"terminal.integrated.profiles.windows": {

"PowerShell -NoProfile": {

"source": "PowerShell",

"args": ["-NoProfile"]

},

"Git-Bash": {

"path": "E:\\program file\\Git\\bin\\bash.exe", # 本地安装的路径

"args": []

}

},

"terminal.integrated.defaultProfile.windows": "Git-Bash"
~~~



## 设置 IDEA、Studio 默认使用 Zsh

![](https://blog.xlxs.top/upload/2024/09/image-20240920020917000.png)

![](https://blog.xlxs.top/upload/2024/09/image-20240920021039754.png)

重启 IDE 生效即为最新 Terminal



> 参考：[Windows安装 Zsh 终端](https://blog.xlxs.top/archives/windows%E5%AE%89%E8%A3%85zsh%E7%BB%88%E7%AB%AF)
