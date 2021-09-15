# Macos配置

## Homebrew配置

官方安装命令：

```shell
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

设置国内源并安装：

```shell
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.ustc.edu.cn/brew.git"
export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.ustc.edu.cn/homebrew-core.git"
/bin/bash -c "$(curl -fsSL https://cdn.jsdelivr.net/gh/ineo6/homebrew-install/install.sh)"
```

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

## 删除自带输入法

1. 将文件`~/Library/Preferences/com.apple.HIToolbox.plist`转换为json格式：

```
plutil -convert json ~/Library/Preferences/com.apple.HIToolbox.plist -o plist.json
```

2. 删除`AppleEnabledInputSources`数组中除了想要的输入法之外的项：

```json
{"AppleCurrentKeyboardLayoutInputSourceID":"com.apple.keylayout.US","AppleEnabledInputSources":[{"InputSourceKind":"Input Mode","Bundle ID":"com.sogou.inputmethod.sogou","Input Mode":"com.sogou.inputmethod.pinyin"},{"InputSourceKind":"Keyboard Input Method","Bundle ID":"com.sogou.inputmethod.sogou"}],"AppleCapsLockPressAndHoldToggleOff":false,"AppleGlobalTextInputProperties":{"TextInputGlobalPropertyPerContextInput":false},"AppleDictationAutoEnable":0,"AppleInputSourceHistory":[{"InputSourceKind":"Input Mode","Bundle ID":"com.sogou.inputmethod.sogou","Input Mode":"com.sogou.inputmethod.pinyin"},{"InputSourceKind":"Keyboard Layout","KeyboardLayout Name":"ABC","KeyboardLayout ID":252}],"AppleSelectedInputSources":[{"InputSourceKind":"Non Keyboard Input Method","Bundle ID":"com.apple.PressAndHold"},{"InputSourceKind":"Input Mode","Bundle ID":"com.sogou.inputmethod.sogou","Input Mode":"com.sogou.inputmethod.pinyin"}],"AppleHandwritingDisabledInputSources":["com.apple.inputmethod.SCIM"]}
```

3. 覆盖原始文件：

```
plutil -convert xml1 plist.json -o ~/Library/Preferences/com.apple.HIToolbox.plist
```

4. 关闭下SIP安全设置：
   1. 重启 Mac，按住 Command+R 键直到 Apple logo 出现，进入 Recovery Mode
   2. 点击 Utilities -> Terminal
   3. 在 Terminal 中输入 `csrutil disable`
   4. 重启 Mac

