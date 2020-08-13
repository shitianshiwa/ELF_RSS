# ELF_RSS

rss订阅插件始终没找到个合适自己的，就自己写了一个。
可以实现推特（twitter）转发、YouTube转发、B站直播提醒、Pixiv每日排行榜推送等等功能

## 功能简介
**管理员qq发送信息到机器人进行添加、删除、修改、查询订阅**

* 短链接生成

* 支持多种订阅源，主要兼容RSSHub生成的订阅源

* 完美兼容酷Q Pro，理论上兼容酷Q Air，但会无法发送图片。

### 更多信息 请移步 [Wiki](https://github.com/Quan666/ELF_RSS/wiki)
* [Home](https://github.com/Quan666/ELF_RSS/wiki)
* [更新日志](https://github.com/Quan666/ELF_RSS/wiki/%E6%9B%B4%E6%96%B0%E6%97%A5%E5%BF%97)
* [功能介绍](https://github.com/Quan666/ELF_RSS/wiki/%E5%8A%9F%E8%83%BD%E4%BB%8B%E7%BB%8D)
* [使用教程](https://github.com/Quan666/ELF_RSS/wiki/%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B)
* [部署教程](https://github.com/Quan666/ELF_RSS/wiki/%E9%83%A8%E7%BD%B2%E6%95%99%E7%A8%8B)
* [常见问题](https://github.com/Quan666/ELF_RSS/wiki/%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98)

如果 Wiki 没更新，请移步 **[ELF_RSS 订阅插件使用、安装教程](https://myelf.club/index.php/archives/221/ "ELF_RSS 订阅插件使用、安装教程")**

### 感谢以下项目或服务

* [RSSHub](https://github.com/DIYgod/RSSHub)
* [Nonebot](https://github.com/richardchien/nonebot)
* [酷Q](https://cqp.cc/)
* [coolq-http-api](https://github.com/richardchien/coolq-http-api)


### 效果预览
![](https://cdn.jsdelivr.net/gh/Quan666/CDN@master/pic/elfrss_1.png)
![](https://cdn.jsdelivr.net/gh/Quan666/CDN@master/pic/elfrss_2.png)
![](https://cdn.jsdelivr.net/gh/Quan666/CDN@master/pic/elfrss_3.png)


使用教程
添加订阅
添加订阅所有提到可选参数都只能从后面开始省略，不能设置在代理时省略更新频率的参数，设置第三方时省略更新频率、代理参数

向机器人发送

add mytwitter /twitter/user/Huagequan 123456,23445 -1 5 1 0

# 以下为注释

# add是添加订阅命令，若单独发送了add后，根据提示填写订阅信息即可，无需再加add

# mytwitt 为订阅名 因为要根据名字生成文件，所以不能有文件名不允许的特殊字符存在
# 不能命名为rss，会与配置文件冲突！！！

# /twitter/user/Huagequan 为订阅地址，此处为rsshub路由地址，非rsshub订阅源要写完整
# 如 https://myelf.club/index.php/feed/ 同时要设置第三方为1

# 123456,23445为订阅者qq号，逗号分开，-1表示设为空

# -1 为订阅群号，和qq号一样英文逗号分开，-1表示为空。
# qq号，群号两者必须有一个不为空，且有效，否则会出错。

# 5 为检查更新的频率，单位分钟/次，最小一分钟，还受到订阅源缓存影响 可选，默认为5

# 1 是否开启代理，有两种参数0/1 1开启，0关闭，设置此项为一必须设置好代理，此项可选，默认为0不开启

# 0 是否第三方订阅，即非rsshub订阅源时必须设为1  可选，默认为0关闭

# 0 翻译，Google翻译，效果一般  可选，默认为0关闭

# 0 仅输出标题，在正文较长的情况下建议启用  可选，默认为0关闭

# 可选参数建议添加订阅成功后通过change修改
机器人回复成功则添加成功。

查看订阅
向机器人发送 show_all 或showall、seeall 即可查看所有订阅

向机器人发送 show test 即可查看某一个订阅详细信息 test为订阅名或者订阅链接

删除订阅
向机器人发送 deldy test 即可删除某一个订阅 test为订阅名或者订阅链接

修改订阅
向机器人发送 change 即可查看修改方法

输入要修改的订阅的 
订阅名 修改项=,属性 
如:
test dyqq=,xx dsf=0
对应参数： 订阅地址-url，订阅QQ-dyqq，订阅群-dyqun，更新频率-uptime，代理-proxy，第三方-dsf，翻译-tl，仅title-ot

注：
代理、第三方、翻译、仅title属性值为1/0
qq、群号前加英文逗号表示追加
test为订阅名 也可直接在change后面加修改参数，也可单独修改某一个参数

短链接
发送 短链 https://myelf.club 即可获得短链接


const cqimgpath = images.map(imgPath => {
                return `[CQ:image,file=file:///Z:home\\user\\coolq\\rsshub2qq-master\\${imgPath.match(/\/tmp\/(\S*)/)[1]}]`
            })