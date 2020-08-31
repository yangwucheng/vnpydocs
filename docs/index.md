# centos yum 源替换为阿里云镜像

https://developer.aliyun.com/mirror/centos?spm=a2c6h.13651102.0.0.3e221b11n3PC8E

```bash
cd /etc/yum.repos.d/
# 备份
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
# 获取阿里云源
wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-8.repo
# 清除缓存
yum clean all
# 生成新缓存
yum makecache
```

# 安装编译工具

vnpy依赖于ta-lib，python3.7。ta-lib，python3.7编译需要gcc等一系列工具，执行以下命令安装编译ta-lib所需的工具

```bash
# 安装开发者工具组
yum -y groupinstall "Development Tools"
yum -y install zlib* openssl-devel zlib-devel libffi-devel libpq-devel python3-devel
```

# 安装python3.7

确认python版本

```bash
python -V
# 或者
python3 -V
```

如果python版本不是3.7，按照如下步骤安装python3.7

```bash
cd ~
wget https://www.python.org/ftp/python/3.7.9/Python-3.7.9.tgz
tar -zxvf Python-3.7.9.tgz
cd Python-3.7.9
./configure
make
make install
```

```bash
cd /etc/alternatives
rm -f pip-3 pip3 pydoc-3 pydoc3 python3 python3-config python3-man pyvenv-3

ln -s /usr/local/bin/pip3.7 /etc/alternatives/pip3
ln -s /usr/local/bin/pydoc3.7 /etc/alternatives/pydoc3
ln -s /usr/local/bin/python3.7 /etc/alternatives/python3
ln -s /usr/local/bin/python3.7 /usr/bin/python
ln -s /usr/local/bin/python3.7-config /etc/alternatives/python3-config
ln -s /usr/local/share/man/man1/python3.7.1 /etc/alternatives/python3-man
ln -s /usr/local/bin/pyvenv-3.7 /etc/alternatives/pyvenv-3
ln -s /usr/local/bin/pip3.7 /usr/local/bin/pip
```



## 设置pypi镜像为清华源

https://mirrors.tuna.tsinghua.edu.cn/help/pypi/

```bash
pip install pip -U
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```



# 安装ta-lib

```bash
cd ~
wget http://prdownloads.sourceforge.net/ta-lib/ta-lib-0.4.0-src.tar.gz
tar -zxvf ta-lib-0.4.0-src.tar.gz
cd ta-lib
./configure --prefix=/usr
make
make install
```

# 安装vnpy

```bash
cd ~
wget https://github.com/vnpy/vnpy/archive/v2.1.5.tar.gz
tar -zxvf v2.1.5.tar.gz
cd vnpy-2.1.5
bash install.sh
```

# 安装MongoDB

https://www.runoob.com/mongodb/mongodb-linux-install.html

```bash
tar -zxvf mongodb-linux-x86_64-rhel80-4.4.0.tgz
export PATH=<mongodb-install-directory>/bin:$PATH
sudo mkdir -p /var/lib/mongo
sudo mkdir -p /var/log/mongodb
sudo chown `whoami` /var/lib/mongo     # 设置权限
sudo chown `whoami` /var/log/mongodb   # 设置权限
mongod --dbpath /var/lib/mongo --logpath /var/log/mongodb/mongod.log --fork
```

