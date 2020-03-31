---
title: "如何用 hugo 搭建个人博客"
date: 2020-03-31T22:18:03+08:00
draft: false
---

# 如何用 hugo 搭建个人博客

什么是hugo？

hugo是一个用Go语言实现的一个博客生成器，我们可以使用hugo搭建一个属于我
们自己的博客网站。

使用hugo搭建个人博客需要以下几步操作：

1. 通过hugo搭建一个博客生成器来撰写博客；
2. 把撰写的博客上传到github的仓库，通过github pages就可以进行浏览了；
3. 购买自己的域名连接到github上，这样就可以把你的博客放到你专属的网站上了。

# 搭建hugo博客生成器

* [下载hugo]([baidu.com](https://github.com/gohugoio/hugo/releases))

1. hugo下载完成以后，建议将hugo.exe放到 D:\Software\hugo 路径中，然后将此路径放到环境变量中。(按下图操作)

![](/static/images/path.png)

1. 重启cmder，运行“hugo version”。我们可以看到安装的hugo的版本号。

````
λ hugo version
Hugo Static Site Generator v0.68.3-157669A0 windows/amd64 BuildDate: 2020-03-24T12:04:36Z
````
* 搭建hugo博客编辑器
  
1. cmder进入一个空文件夹，执行以下代码（[参考官网](https://gohugo.io/getting-started/quick-start/)）
````
hugo new site github用户名（小写）.github.io-creater
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
echo 'theme = "ananke"' >> config.toml
hugo new posts/博客名.md
````

2. 进入.md文件，撰写你的第一篇博客。（可以先随便写一点）
   
   这里需要注意：将draft改为false
  
![](/static/images/draft.png)

1. 将config.toml中进行如下图更改。
   

![](/static/images/config.png)



4. 运行 hugo server -D，进入 http://localhost:1313/ 我们会看到，我们的hugo博客已经搭建好了。

````
λ hugo server -D
Building sites … WARN 2020/03/31 20:35:57 Page.URL is deprecated and will be removed in a future release. Use .Permali nk or .RelPermalink. If what you want is the front matter URL value, use .Params.url

                   | EN
-------------------+-----
  Pages            | 12
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  5
  Processed images |  0
  Aliases          |  1
  Sitemaps         |  1
  Cleaned          |  0

Built in 35 ms
Watching for changes in D:\jirengu\h666t.github.io-creator\{archetypes,content,data,layouts,static,themes}
Watching for config changes in D:\jirengu\h666t.github.io-creator\config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
````

5. 我们可以向github远程仓库推送一份代码作为博客编辑器的备份。

#### 完成以上步骤以后我们就可以在本地浏览我们的博客了。


# 将博客上传到github，使其可以被他人浏览

* 将博客上传到github

1. 在cmder运行Hugo，这时，我们会发现文件夹内多了一个public的文件夹，这个public文件夹就是我们要用来展示的博客。（我们需要写一个.gitignore文件来避免public和博客编辑器一起被推送到同一个github仓库）

![](/static/images/.ignore.png)

2. 此时我们可以建立一个github远程仓库（仓库名字必须为：用户名（小写）.github.io）,然后将public推送到该仓库。

* 通过github网址浏览

进入 用户名.github.io 的 settings选项，找到GitHub Pages，将旁边的链接分享给他人，我们可以发现，他人也可以通过github的链接浏览你的博客了。

![1](/static/images/reposetting.png)


# 将你的博客放到属于你的网站上

* 通过[namesilo](https://www.namesilo.com/)或者[阿里云](https://wanwang.aliyun.com/domain/recommend#/?keyword=xww)购买一个域名

* 进入[github](https://help.github.com/cn/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain),找到apex domain的ip地址
![](/static/images/ip.png)

* 配置解析设置：以阿里云为例，将ip地址分别添加到购买的域名中。（按下图操作，得到图4）
![](/static/images/apex.png)

* 在命令行输入nslookup 域名，测试解析设置是否成功，若返回四个IP地址，则说明成功，否则，可等一段时间在测试一下。

````
λ nslookup huanghaotian.top
服务器:  192.168.1.1
Address:  192.168.1.1

非权威应答:
名称:    huanghaotian.top
Addresses:  185.199.110.153
          185.199.108.153
          185.199.109.153
          185.199.111.153
````
  
* 将你的域名填入github pages中储存一下，你就拥有了一个属于你自己的博客网站了。

![](/static/images/suc.png)

#### 当我们需要写新博客时，我们只需要在D:\jirengu\h666t.github.io-creator\content\posts 路径中复制一个md文件，编写完成后上传到github仓库，就可以在我们的网站上正常浏览啦！