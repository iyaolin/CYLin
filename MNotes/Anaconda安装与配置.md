# Anaconda安装与配置
@[mac]

[TOC]

YLin的Mac环境配置系列

**`参考资料`**

- 无

## 安装

```shell
#下载和安装
wget https://repo.continuum.io/archive/Anaconda3-5.1.0-Linux-x86_64.sh
bash Anaconda3-5.1.0-Linux-x86_64.sh

#Anaconda安装好后，可以看到系统会多出个 ~/anaconda 目录，安装程序会把bin目录加入PATH（写入~/.bashrc)。

#如果安装时没有自动写上，可手动添加
# 将anaconda的bin目录加入PATH
echo 'export PATH="~/anaconda3/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

## 配置
配置conda使用清华大学开源镜像

```shell
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes

#测试
conda info
```

## 卸载
卸载Anaconda3：[How to uninstall Anaconda completely from MacOS](https://stackoverflow.com/questions/42182706/how-to-uninstall-anaconda-completely-from-macos)

```shell
rm -rf ~/anaconda*
rm -rf ~/.condarc ~/.conda ~/.continuum
```

