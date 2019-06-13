# 1. 安装Hexo

## 1.1 安装git
成功后, 在命令行查看：    
``` bash
$ git --help     
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]       
.......    
```

## 1.2 安装Node.js
windows直接安装LTS版本即可，成功后，在命令行查看：    
``` bash
$ node -v    
v10.16.0
$ npm -v     
6.9.0
```

## 1.3 安装Hexo
1. 新建文件夹，安装Hexo：     
``` bash
$ npm inst$ npm install -g hexo-cli
C:\Users\exgxxln\AppData\Roaming\npm\hexo -> C:\Users\exgxxln\AppData\Roaming\npm\node_modules\hexo-cli\bin\hexo
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.9 (node_modules\hexo-cli\node_modules\fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.9: wanted {"os":"darwin","arch":"any"} (current: {"os":"win32","arch":"x64"})

+ hexo-cli@2.0.0
updated 1 package in 5.405s
``` 
2. 成功后，查看：    
``` bash
$ hexo -v
hexo-cli: 2.0.0
os: Windows_NT 10.0.16299 win32 x64
http_parser: 2.8.0
node: 10.16.0
v8: 6.8.275.32-node.52
uv: 1.28.0
zlib: 1.2.11
brotli: 1.0.7
ares: 1.15.0
modules: 64
nghttp2: 1.34.0
napi: 4
openssl: 1.1.1b
icu: 64.2
unicode: 12.1
cldr: 35.1
tz: 2019a
```

3. 初始化

``` bash
# 使用WIN10自带的命令行 ==> MINGW可能会有些问题
$ hexo "init StarBlog"
.....
found 2 low severity vulnerabilities
  run `npm audit fix` to fix them, or `npm audit` for details
INFO  Start blogging with Hexo!

```

4. 安装
``` bash
$ cd StarBlog/
$ npm install
audited 4697 packages in 3.6s
found 2 low severity vulnerabilities
  run `npm audit fix` to fix them, or `npm audit` for details

$ npm audit fix
up to date in 1.457s
fixed 0 of 2 vulnerabilities in 4697 scanned packages
  2 vulnerabilities required manual review and could not be updated
```
5. 生产静态blog
``` bash
$ hexo generate(g)
INFO  Start processing
INFO  Files loaded in 230 ms
INFO  Generated: index.html
INFO  Generated: archives/index.html
INFO  Generated: fancybox/blank.gif
INFO  Generated: fancybox/fancybox_loading@2x.gif
INFO  Generated: fancybox/fancybox_overlay.png
INFO  Generated: fancybox/fancybox_loading.gif
INFO  Generated: fancybox/fancybox_sprite.png
INFO  Generated: fancybox/fancybox_sprite@2x.png
INFO  Generated: fancybox/helpers/jquery.fancybox-buttons.css
INFO  Generated: archives/2019/05/index.html
INFO  Generated: js/script.js
INFO  Generated: fancybox/helpers/jquery.fancybox-thumbs.css
INFO  Generated: fancybox/jquery.fancybox.css
INFO  Generated: css/style.css
INFO  Generated: archives/2019/index.html
INFO  Generated: fancybox/helpers/jquery.fancybox-buttons.js
INFO  Generated: fancybox/helpers/fancybox_buttons.png
INFO  Generated: fancybox/jquery.fancybox.pack.js
INFO  Generated: css/fonts/fontawesome-webfont.eot
INFO  Generated: css/fonts/fontawesome-webfont.woff
INFO  Generated: css/fonts/fontawesome-webfont.ttf
INFO  Generated: fancybox/helpers/jquery.fancybox-media.js
INFO  Generated: fancybox/helpers/jquery.fancybox-thumbs.js
INFO  Generated: css/fonts/FontAwesome.otf
INFO  Generated: fancybox/jquery.fancybox.js
INFO  Generated: css/fonts/fontawesome-webfont.svg
INFO  Generated: css/images/banner.jpg
INFO  Generated: 2019/05/31/hello-world/index.html
INFO  28 files generated in 493 ms
```

6. 目录结构
``` bash
 _config.yml   --> 博客的配置文件
 db.json     
 node_modules/ --> 依赖包
 package.json
 package-lock.json
 public/       --> 存放生成的页面
 scaffolds/    --> 生成文章的一些模板
 source/       --> 存放你的文章
 themes/       --> 主题
```

7. 启动
``` bash
$ hexo server(s)
```

======
## 1.4 链接插件
1. 安装修改链接插件
``` bash
$ npm install "hexo-abbrlink --save"
```
2. 修改_config.xml文件
``` xml
permalink: :category/:abbrlink.html  // category是文章开头指定的类别
abbrlink:
  alg: crc32  # Alogrithm：crc16(default) and crc32
  rep: hex    # Decimal：dec(default) and hex
```
3. 查看结果
``` bash
$ hexo g
$ hexo s

链接显示为：
http://localhost:4000/testfirst/2f8dc138.html
```

======
## 1.5 部署插件
1. 安装插件
``` bash
$ npm install "hexo-deployer-git --save"
```
2. 在github创建repo，命名格式为：githubusername.github.io

3. 修改_config.xml文件
``` xml
deploy:
  type: git
  repo: https://github.com/liustarsun/liustarsun.github.io.git
  branch: master
```

**github repo必须设置为public的，如果是private的，则需要交钱才可以使用gitpage托管**

======
## 1.6 Hexo基本配置
1. 换theme
``` bash
$ cd themes
$ git clone "https://github.com/theme-next/hexo-theme-next.git"

```

2. 修改_config.xml文件
``` xml
theme: next # 目录名字和themes目录下面的名字相同
```

======
1. 修改文章模板
``` bash
 # scaffolds/ 目录下面的三个模板
 $ hexo new "[layout=page, post, draft] <title>"
```