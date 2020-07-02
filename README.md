

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


2. Install Jekyll and [bundler][jekyll-ruby-101-bundler] [gems][jekyll-ruby-101-gems].

```sh
gem install jekyll bundler
```


3. Clone the project from GitHub.

```sh
git clone https://github.com/qianzhiweisppc/qianzhiweisppc.github.io
```


4. Change into the project directory.
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



7. Now browse to [http://localhost:4000][localhost-4000].


8. 服务器重启后需重启运行命令

```sh
cd qianzhiweisppc.github.io
```

```sh
bundle exec jekyll serve -H 0.0.0.0 -P 4000 --detach
```
