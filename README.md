macOs(m1)常见问题及技巧
====================

<a id="toc" name="toc">目录</a>

<!-- TOC -->

- [初步使用及配置问题](#初步使用及配置问题)
    - [Finder(访达)](#finder访达)
        - [显示隐藏文件](#显示隐藏文件)
        - [默认显示列表视图](#默认显示列表视图)
    - [自定义快捷键](#自定义快捷键)
    - [设置启动台launchpad上的图标大小](#设置启动台launchpad上的图标大小)
    - [显示桌面的快捷键](#显示桌面的快捷键)
    - [终端](#终端)
        - [自定义提示符](#自定义提示符)
        - [表格示例](#表格示例)

<!-- /TOC -->

# 初步使用及配置问题

## Finder(访达)

### 显示隐藏文件

如何在Mac上显示隐藏文件？

1. 临时显示
    - 从打开Finder开始。 接下来，转到主文件夹。 您可以访问左栏中“设备”下的主文件夹。
    - 按键盘键Cmd + Shift +。 （点）。 只要按下此组合键，就会看到所有隐藏的文件夹和文件。
    - 如果您需要再次隐藏这些文件，您只需再次按下该组合即可。
1. 更改系统配置

    在终端使用:
    ```
    //显示隐藏文件
    defaults write com.apple.finder AppleShowAllFiles -bool true
    //不显示隐藏文件
    defaults write com.apple.finder AppleShowAllFiles -bool false
    ```

    最后需要重启Finder:

    重启Finder：窗口左上角的苹果标志-->强制退出-->Finder-->重新启动

### 默认显示列表视图

打开访达，顶部菜单显示，查看显示选项。

## 自定义快捷键

![plugin img](imgs/cshortcutkey.png?raw=true)

## 设置启动台launchpad上的图标大小

事实上是设置启动台图标的行数和列数。默认是5行7列。

Copy and paste the below command and hit enter:

```
defaults write com.apple.dock springboard-rows -int 6
defaults write com.apple.dock springboard-columns -int 9
killall Dock
```
## 显示桌面的快捷键

Command+F3，其中F3单独使用是调度中心。Mission Control。

## 终端

### 自定义提示符

- Open the terminal
- Type touch ~/.zshrc to create the file.
- Open the ~/.zshrc file using vim, nedit, or any other text editor. If you’re accessing the file through Finder, use Cmd + Shift + . to show the hidden files. You’ll want to add the PROMPT variable to this file, as described below.

SEE：

[Customize the MacOS Terminal PDF](pdfs/CustomizeMacOSTerminal.pdf?raw=true)

[zsh prompt documentation](http://zsh.sourceforge.net/Doc/Release/Prompt-Expansion.html#Prompt-Expansion)

OR:

[Customize the MacOS Terminal ORIGION Artical](https://medium.com/dev-genius/customize-the-macos-terminal-zsh-4cb387e4f447)

默认提示符为：

PROMPT='%n@%m %. %% '

Explanation of components:

```
%n  $USERNAME
%m  The hostname up to the first ‘.’
%.  Current directory
%%  Character '%'
```

设置为：`echo $PROMPT`

    %D %*:%~ %%

效果如下：

    21-01-27 0:57:04:/usr/local % ls

### 表格示例

下表展示了 Rust 内建的整数类型。在有符号列和无符号列中的每一个变体（例如，i16）都可以用来声明整数值的类型。

表格: Rust 中的整型

| 长度 | 有符号 | 无符号 |
| ------ | ------ | ------ |
| 8-bit | i8 | u8 |
| 16-bit | i16 | u16 |
| 32-bit	|i32	|u32|
|64-bit	|i64	|u64|
|128-bit	|i128|	u128|
|arch	|isize|	usize|