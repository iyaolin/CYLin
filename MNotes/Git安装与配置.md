# Git安装与配置
@[mac]

[TOC]


**`参考资料`**

- [初次安装git配置用户名和邮箱](https://www.cnblogs.com/superGG1990/p/6844952.html)




## 安装与初始化
mac已默认安装好git, 但初次使用需要运行命令来配置用户名和邮箱。

```shell
git config --global user.name "yaolin"
git config --global user.email "yaolin.bnu@gmail.com"
#注：此用户名和邮箱是git提交代码时用来显示你身份和联系方式的，并不是github用户名和邮箱。
```

## 配置git使用ssh密钥
git支持https和git两种传输协议，但使用https协议时，每次pull, push都会提示要输入密码，使用git协议，然后使用ssh密钥，这样免去每次都输密码的麻烦。

使用git的用户要使用git协议大概需要三个步骤：

**1. 生成密钥对**

首先确认本机是否已经有一个公钥。SSH公钥默认储存在账户的主目录下的 ~/.ssh目录：

```shell
cd ~/.ssh
ls
```
看一下有没有id_rsa和id_rsa.pub(或者是id_dsa和id_dsa.pub之类成对的文件)，有.pub后缀的文件就是公钥，另一个文件则是密钥。
假如没有这些文件，甚至连.ssh目录都没有，可以用 ssh-keygen 来创建。

```shell
ssh-keygen -t rsa -C "your_email@youremail.com"
#Creates a new ssh key using the provided email # Generating public/private rsa key pair.
```
然后，会提示你输入密码，完了之后，大概是这样：
>Your public key has been saved in /home/you/.ssh/id_rsa.pub. 
The key fingerprint is: # 01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@youremail.com

到此为止，你本地的密钥对就生成了。

**2. 添加公钥到你的远程仓库（github）**

查看你生成的公钥: 

```
cat ~/.ssh/id_rsa.pub
```

登陆你的github帐户。点击你的头像，然后Settings -> 左栏点击 SSH and GPG keys -> 点击 New SSH key。然后你复制上面的公钥内容，粘贴进“Key”文本域内。 title域，自己随便起个名字，点击 Add key。

完成以后，验证下这个key是不是正常工作：

```shell
ssh -T git@github.com
```
如果，看到：
>
Hi xxx! You’ve successfully authenticated, but GitHub does not # provide shell access.

恭喜你，你的设置已经成功了。

**3. 修改git的remote url**
使用命令 git remote -v 查看你当前的 remote url：

```
$ git remote -v 
origin https://github.com/someaccount/someproject.git (fetch) 
origin https://github.com/someaccount/someproject.git (push)
```
使用命令 git remote set-url 来调整你的url:

```
git remote set-url origin git@github.com:someaccount/someproject.git
```
至此，可以愉快的使用git fetch, git pull , git push，再也不用输入烦人的密码。

# git常用命令
## git原理
![git原理](http://www.ruanyifeng.com/blogimg/asset/2014/bg2014061202.jpg)

## 常用命令
Git使用分三种情况，分别是通过git clone获取远程repo，初始化本地目录，使用本地git repo。

#### **1. Create a new repository**

```
git clone http://git.xiaojukeji.com/yaolin/passenger.git #获取远程repo
cd passenger
touch README.md #在本地做修改
git add README.md
git commit -m "add README"
git push -u origin master #将本地修改push到远程repo
```

#### **2. Existing folder**

```
git init
git remote add origin http://git.xiaojukeji.com/yaolin/passenger.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

#### **3. Existing Git repository**

```
git remote add origin http://git.xiaojukeji.com/yaolin/passenger.git
git push -u origin --all
git push -u origin --tags
```

#### **其他常用git命令**

```
git status #查看本地哪些代码进行了修改
git remote -v #查看远程主机及网址
git branch -a #查看所有分支
```