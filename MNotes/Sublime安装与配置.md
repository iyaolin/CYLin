# Sublime安装与配置
@[mac]

[TOC]

YLin的Mac环境配置系列

**`参考资料`**

- 无 

## 安装
从[官网](http://www.sublimetext.com/)下载最新版安装；

## 安装插件管理器

通过`ctrl+`或`View > Show Console`启动console, 输入：

```python
import urllib.request,os,hashlib; h = '6f4c264a24d933ce70df5dedcf1dcaee' + 'ebe013ee18cced0ef93d5f746d80ef60'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```
## 安装插件

`Ctrl+Shift+P`，输入`install`，等待几秒后出现插件列表，输插件名再回车就能自动安装。
```
Pretty JSON
ConvertToUTF8
SideBarEnhancements
Theme - Flatland
```

## 配置主题
点击`Preference-Settings`，修改内容为：

```
{
    "color_scheme": "Packages/Theme - Flatland/Flatland Monokai.tmTheme",
    "font_face": "Monaco",
    "font_size": 13,
    "ignored_packages":
    [
        "Vintage",
        "Markdown"
    ],
    "line_numbers": true,
    "line_padding_bottom": 2,
    "open_files_in_new_window": false,
    "remember_full_screen": false,
    "theme": "Flatland Dark.sublime-theme"
}
```


# Sublime常见问题
## 1. 在终端用Sublime打开文件
 
参考资料： [Launch Sublime Text 2 or 3 from the Mac OSX Terminal](https://ashleynolan.co.uk/blog/launching-sublime-from-the-terminal)

```
ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/sublime
#修改bash_profile
# vim ~/.bash_profile
# export PATH=/usr/local/bin:$PATH
#测试
subl 
```

## 2. 文本自动对齐
 
安装 **`Alignment`**插件，安装后选中文本按`cmd + ctl + a`。
