

### Quick Start

1. 安装Ruby环境

1.1 安装RVM

```sh
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
```

```sh
curl -sSL https://get.rvm.io | bash -s stable
```

```sh
source /etc/profile.d/rvm.sh
```

检查RVM是否安装正确
```sh
rvm -v
```


1.2用 RVM 安装 Ruby 环境

列出已知的 ruby 版本:
```sh
rvm list known
```

可以选择现有的 rvm 版本来进行安装
```sh
rvm install 2.6.3
```

设置 Ruby 版本
RVM 装好以后，需要执行下面的命令将指定版本的 Ruby 设置为系统默认版本
```sh
rvm 2.6.3 --default
```


rvm 常用命令

查询已经安装的 ruby
```sh
rvm list
```

卸载一个已安装版本
```sh
rvm remove 1.9.2
```

检查版本是否安全正确
```sh
ruby -v
```

```sh
gem -v
```


2. 安装 Jekyll and [bundler] [jekyll-ruby-101-bundler] [gems][jekyll-ruby-101-gems].

```sh
gem install jekyll bundler
```


3. Clone 项目 from GitHub

```sh
git clone https://github.com/qianzhiweisppc/qianzhiweisppc.github.io
```


4. 进入目录
```sh
cd qianzhiweisppc.github.io
```


5. Install required gems in the `Gemfile` using Bundler.
```sh
bundle install
```


6. Build the site and make it available on a local server.
```sh
bundle exec jekyll serve -H 0.0.0.0 -P 4000 --detach 
```

注意后面一定要指定参数，jekyll 默认绑定了 127.0.0.1 的地址，导致不加参数直接运行的话，是无法访问项目的。

-H 表示绑定到本机 IP

-P 表示指定端口，根据自己需求修改 

--detach 表示后台运行

#调试时可不加后台运行参数，这样直接 Ctrl+C 就能关闭进程



7. 现场打开网页就可访问 http://localhost:4000


8. 服务器重启后需重启运行命令

```sh
cd qianzhiweisppc.github.io
```

```sh
bundle exec jekyll serve -H 0.0.0.0 -P 4000 --detach
```

9. 也可以直接把编译完成的_site文件夹内容放在网站根目录，直接访问，如果需要修改首页标题这类，可以编辑网站根目录下的_config.yml 文件，网址的话则是修改_data 目录下的 links.yml，还有各种页面相关信息也是修改此目录下其他文件即可。

10. 前端库默认使用unpkg.com，可以换成国内前端库，或者 cdn.jsdelivr.net/npm/ ,国内有加速CDN

11. 页面的今日访客和当前在线等统计数据需要显示的话，用docker安装 Matomo

11.1 安装docker

```sh
#CentOS 6
rpm -iUvh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
yum update -y
yum -y install docker-io
service docker start
chkconfig docker on

#CentOS 7、Debian、Ubuntu
curl -sSL https://get.docker.com/ | sh
systemctl start docker
systemctl enable docker
```

11.2 拉取matomo镜像和MySQL镜像（如果你服务器已经安装过Mysql数据库，可以跳过该步骤）

```sh
docker pull crazymax/matomo

docker pull mysql:5.6 
```

11.3 创建matomo容器，把容器里 data 目录和 8000 端口映射出来：

```sh
docker run --restart=always -d --name matomo -p 8000:8000 -v /matomo/data:/data crazymax/matomo
```

11.4 创建 MySQL 容器，3306 端口和对应目录也映射出来，用户名/数据库名这类按自己需求修改（如果你服务器已经安装过Mysql数据库，可以跳过该步骤）

```sh
docker run --restart=always --name mysql -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=lishuma -e MYSQL_DATABASE=matomo -e MYSQL_USER=matomo -e MYSQL_PASSWORD=matomo -v /matomo/mysql:/var/lib/mysql mysql:5.6
```

11.5 防火墙放行 8000 和 3306 端口，然后访问 IP+8000 端口即可看到 Matomo 界面。

11.6 一路下一步，数据库信息按照自己设定的填写即可，注意服务器地址填写外部物理机的 IP。

11.7  网站地址直接写 IP 有个问题就是程序会提示不安全，需要修改/root/matomo/data/config/config.ini.php：

```sh
enable_trusted_host_check=0
```

或者
修改trusted_hosts[]参数为你的访问地址

11.8 配置该导航的话，需要修改配置文件_data/analytics.yml，大致参数如下：
#url为matomo站点，domain为导航站，site_id为matomo站点统计站id，token为matomo站点的token

```sh
matomo:
  url: http://matomo.qianzhiweisppc.com/
  domains:
  - "http://byr.qianzhiweisppc.com"
  site_id: 1
  token: 297bd600834c2a5a70293c47a
```

参数获取大致路径如下：

```sh
1、site_id
在后台添加一个网站统计，就可以直接看到网站id
2、token
该参数可以在Settings里获取API Authentication Token
```

11.9 最后统计站的通用设置里还需要设置一下跨域资源共享，填上导航站的地址，保存退出即可：




-----------------------------------------------------------------------------------------------------
备用
centOS下进程的后台运行、查看进程、结束进程

1、查看进程

#ps -aux | grep nginx*

上述命令表示查看nginx相关的进程

2、杀死进程

#kill -9 7819

上述命令表示杀死pid为7819的进程

-----------------------------------------------------------------------------------------------------

netstat -lntp    #查看监听(Listen)的端口

netstat -antp   #查看所有建立的TCP连接

netstat -tulpn  #查看所有运行中的服务的详细信息

ps -ef              #查看所有进程

ps -aux           #查看使用内存的进程

top                  #查看内存使用说明 (shift+m 按照排名)

kill -pid  #结束进程：




