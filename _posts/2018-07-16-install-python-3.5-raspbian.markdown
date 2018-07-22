---
layout: post
title: "如何在Raspbian上安装Python3.7"
date: 2018-07-16 10:45:41 +0800
categories: python raspbian
permalink: /installing-python-3.7-on-raspbian/
---
从2016年10月开始, Raspbian 将不再安装最新的 Python,这意味着你需要自己安装，本文教你如何进行安装。

安装如下安装包：

```
sudo apt-get update
sudo apt-get install build-essential tk-dev
sudo apt-get install libncurses5-dev libncursesw5-dev libreadline6-dev
sudo apt-get install libdb5.3-dev libgdbm-dev libsqlite3-dev libssl-dev
sudo apt-get install libbz2-dev libexpat1-dev liblzma-dev zlib1g-dev
```

如果有的安装包无法安装，请尝试新版的安装包（例如：用libdb5.4-dev来替换libdb5.3-dev）。

上述软件包只有在需要的时候安装，如果你的系统中安装了这些软件包，甚至可以直接安装 Python。

下载与安装 Python 3.7，下载最新的 Python 3.7源程序。

```
wget https://www.python.org/ftp/python/3.7.0/Python-3.7.0.tgz
tar zxvf Python-3.7.0.tgz
cd Python-3.7.0
./configure --prefix=/usr/local/opt/python-3.7.0
make
sudo make install
```

执行以下命令以确保可以在全局调用Python和Python相关程序。

```
sudo ln -s /usr/local/opt/python-3.7.0/bin/pydoc3.7 /usr/bin/pydoc3.7
sudo ln -s /usr/local/opt/python-3.7.0/bin/python3.7 /usr/bin/python3.7
sudo ln -s /usr/local/opt/python-3.7.0/bin/python3.7m /usr/bin/python3.7m
sudo ln -s /usr/local/opt/python-3.7.0/bin/pyvenv-3.7 /usr/bin/pyvenv-3.7
sudo ln -s /usr/local/opt/python-3.7.0/bin/pip3.7 /usr/bin/pip3.7
```

至此，你已在树莓派上完成了Python3.7的安装！

另外，你也许需要删除该源码和编译它依赖的软件包。

```
sudo rm -r Python-3.7.0
rm Python-3.7.0.tgz
sudo apt-get --purge remove build-essential tk-dev
sudo apt-get --purge remove libncurses5-dev libncursesw5-dev libreadline6-dev
sudo apt-get --purge remove libdb5.3-dev libgdbm-dev libsqlite3-dev libssl-dev
sudo apt-get --purge remove libbz2-dev libexpat1-dev liblzma-dev zlib1g-dev
sudo apt-get autoremove
sudo apt-get clean
```

参考：
https://liudr.wordpress.com/2016/02/04/install-python-on-raspberry-pi-or-debian/
