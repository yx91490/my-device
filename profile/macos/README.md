# Macos配置

## 命令行配置

安装必要软件：

```
$ brew reinstall bash-completion@2
```

更改bash：

```
$ chsh -s /usr/local/bin/bash
$ sudo chsh -s /usr/local/bin/bash
```

配置`/etc/profile`：

```
# vim /etc/profile
[[ -f "$HOME/.bashrc" ]] && . $HOME/.bashrc
```

### 参考

- [How to set my default shell on Mac?](https://stackoverflow.com/questions/453236/how-to-set-my-default-shell-on-mac)
- [.bash_profile vs .bashrc](http://www.joshstaiger.org/archives/2005/07/bash_profile_vs.html)
- [What is the difference between .bash_profile and .bashrc?](https://apple.stackexchange.com/questions/51036/what-is-the-difference-between-bash-profile-and-bashrc)
- [我的profile文件](./bashrc)

## Finder

设置：

Finder -> Services -> Services Preferences，选中 "New Terminal at Folder" 和 "New Terminal Tab at Folder"

要在终端中打开Finder中的当前目录,请键入`open .`

## Macos快捷键

| 软件   | 快捷键 | 功能           |
| ------ | ------ | -------------- |
| Finder | ⌘+上   | 前往上层文件夹 |
|        |        |                |
|        |        |                |

- [Mac 键盘快捷键](https://support.apple.com/zh-cn/HT201236)
- [从Finder快速进入当前目录的命令行](https://blog.csdn.net/yasi_xi/article/details/46799535)