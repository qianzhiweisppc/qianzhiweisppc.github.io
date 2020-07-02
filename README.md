

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
rvm install 2.6.
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

设置 Ruby 版本
RVM 装好以后，需要执行下面的命令将指定版本的 Ruby 设置为系统默认版本
```sh
rvm 2.6.3 --default
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
git clone https://github.com/BYR-Navi/BYR-Navi.git
```

4. Change into the project directory.

```sh
cd BYR-Navi
```

5. Install required gems in the `Gemfile` using Bundler.

```sh
bundle install
```

6. Build the site and make it available on a local server.

```sh
bundle exec jekyll serve
```

7. Now browse to [http://localhost:4000][localhost-4000].

## :construction: Deployment

### GitHub Pages (Recommended)
Sites on GitHub Pages are powered by Jekyll behind the scenes, so if you&rsquo;re looking for a zero-hassle, zero-cost solution, GitHub Pages are a great way to [host your Jekyll-powered website for free][jekyll-gihub-pages].

### Manual Deployment
Jekyll generates your static site to the `_site` directory by default. You can transfer the contents of this directory to almost any hosting provider to get your site live.
[Here][jekyll-manual-deployment] are some manual ways of achieving this.

## :hearts: Share the Love
I&rsquo;ve put a lot of time and effort into making **BYR-Navi** awesome.
If you love it, you can buy me a coffee.
Every cup helps!
I promise it will be a good investment.

Donate [here][donate].

## :rocket: Powered by
- [Fomantic UI][fomantic]
- [jQuery][jquery]
- [Shields.io][shields]
- [Day.js][day]
- [CountUp.js][countup]
- [jQuery.countdown][countdown]
- [JavaScript Cookie][js-cookie]
- [url.js][js-url]
- [Hitokoto][hitokoto]
- [ECharts][echarts]
- [Matomo][matomo]
- [GeoIP][geoip]
- [Jekyll][jekyll]
- [Let&rsquo;s Encrypt][letsencrypt]
- [Linode][linode]

## :copyright: License
[MIT License][license]

[travis-ci]: https://travis-ci.org/BYR-Navi/BYR-Navi "Travis CI"
[website]: https://byr-navi.com/ "Website"
[license]: https://github.com/BYR-Navi/BYR-Navi/blob/master/LICENSE "License"
[commit]: https://github.com/BYR-Navi/BYR-Navi/commits/master "Last Commit"
[donate]: https://byr-navi.com/donate/ "Donate"

[fomantic]: https://fomantic-ui.com/ "Fomantic UI"
[fomantic-doc]: https://fomantic-ui.com/introduction/getting-started.html "Fomantic UI Docs"
[jquery]: https://jquery.com/ "jQuery"
[shields]: https://shields.io/ "Shields.io"
[day]: https://github.com/iamkun/dayjs "Day.js"
[countup]: https://inorganik.github.io/countUp.js/ "CountUp.js"
[countdown]: https://hilios.github.io/jQuery.countdown/ "The Final Countdown plugin for jQuery"
[js-cookie]: https://github.com/js-cookie/js-cookie "JavaScript Cookie"
[js-url]: https://github.com/websanova/js-url "url.js"
[hitokoto]: https://hitokoto.cn/api "Hitokoto"
[echarts]: https://echarts.apache.org/ "ECharts"
[matomo]: https://matomo.org/ "Matomo"
[geoip]: https://www.maxmind.com/ "GeoIP"
[jekyll]: https://jekyllrb.com/ "Jekyll"
[jekyll-doc]: https://jekyllrb.com/docs/home/ "Jekyll Docs"
[jekyll-installation]: https://jekyllrb.com/docs/installation/ "Jekyll Installation"
[jekyll-gihub-pages]: https://jekyllrb.com/docs/github-pages/ "Jekyll GitHub Pages"
[jekyll-manual-deployment]: https://jekyllrb.com/docs/deployment/manual/ "Jekyll Manual Deployment"
[jekyll-ruby-101-gems]: https://jekyllrb.com/docs/ruby-101/#gems "Jekyll Ruby 101 Gems"
[jekyll-ruby-101-bundler]: https://jekyllrb.com/docs/ruby-101/#bundler "Jekyll Ruby 101 Bundler"
[localhost-4000]: http://localhost:4000 "Local Host (Port: 4000)"
[github-pages]: https://pages.github.com/ "GitHub Pages"
[letsencrypt]: https://letsencrypt.org/ "Let&rsquo;s Encrypt"
[linode]: https://www.linode.com/ "Linode"

