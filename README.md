* [功能](#功能)
* [输入](#输入)
* [输出](#输出)
* [运行环境](#运行环境)
* [使用说明](#使用说明)
  * [下载脚本](#1下载脚本)
  * [安装依赖](#2安装依赖)
  * [设置cookie和user_id](#3设置cookie和user_id)
  * [运行脚本](#4运行脚本)
  * [按需求修改脚本](#5按需求修改脚本可选)
* [如何获取cookie](#如何获取cookie)
* [如何获取user_id](#如何获取user_id)

# 功能
爬取新浪微博信息，并写入csv/txt文件，文件名为目标用户id加".csv"和".txt"的形式，同时还会下载该微博原始图片和微博视频(可选)。<br>
<br>
本程序需要设置用户cookie，以获取微博访问权限，后面会讲解如何获取cookie。如需免cookie版，大家可以访问<https://github.com/dataabc/weibo-crawler>，
二者功能类似，免cookie版因为不需要cookie，用法更简单，但功能却更多。<br>
<br>
以爬取迪丽热巴的微博为例，她的微博昵称为"Dear-迪丽热巴"，id为1669879400(后面会讲如何获取用户id)。我们选择爬取她的原创微博。程序会自动生成一个weibo文件夹，我们以后爬取的所有微博都被存储在这里。然后程序在该文件夹下生成一个名为"Dear-迪丽热巴"的文件夹，迪丽热巴的所有微博爬取结果都在这里。"Dear-迪丽热巴"文件夹里包含一个csv文件、一个txt文件、一个img文件夹和一个video文件夹，img文件夹用来存储下载到的图片，video文件夹用来存储下载到的视频。<br>
<br>
csv文件结果如下所示：
![](https://picture.cognize.me/cognize/github/weibospider/weibo_csv.png)*1669879400.csv*<br>
<br>
txt文件结果如下所示：
![](https://picture.cognize.me/cognize/github/weibospider/weibo_txt.png)*1669879400.txt*<br>
<br>
下载的图片如下所示：
![](https://picture.cognize.me/cognize/github/weibospider/img.png)*img文件夹*<br>
本次下载了793张图片，大小一共1.21GB，包括她原创微博中的图片和转发微博转发理由中的图片。图片名为yyyymmdd+微博id的形式，若某条微博存在多张图片，则图片名中还会包括它在微博图片中的序号。若某张图片因为网络等原因下载失败，程序则会以“weibo_id:pic_url”的形式将出错微博id和图片url写入同文件夹下的not_downloaded.txt里；<br>
<br>
下载的视频如下所示：
![](https://picture.cognize.me/cognize/github/weibospider/video.png)*video文件夹*<br>
本次下载了70个视频，是她原创微博中的视频，视频名为yyyymmdd+微博id的形式。其中有一个视频因为网络原因下载失败，程序将它的微博id和视频url以“weibo_id:video_url”的形式写到了同文件夹下的not_downloaded.txt里。

# 输入
用户id，例如新浪微博昵称为"Dear-迪丽热巴"的id为"1669879400"

# 输出
- 昵称：用户昵称，
- 微博数：用户的全部微博数
- 关注数：用户关注的微博数量
- 粉丝数：用户的粉丝数
- 微博id：微博唯一标志
- 微博内容：微博正文
- 原始图片url：
- 微博发布位置：位置微博中的发布位置
- 微博发布时间：微博发布时的时间，
- 点赞数：微博被赞的数量
- 转发数：微博被转发的数量
- 评论数：微博被评论的数量
- 微博发布工具：微博的发布工具，如iPhone客户端、HUAWEI Mate 20 Pro等
- 结果文件：保存在当前目录weibo文件夹下以用户昵称为名的文件夹里，名字为"user_id.csv"和"user_id.txt"的形式
- 微博图片：原创微博中的图片和转发微博转发理由中的图片，保存在以用户昵称为名的文件夹下的img文件夹里
- 微博视频：原创微博中的视频，保存在以用户昵称为名的文件夹下的video文件夹里

# 运行环境
- 开发语言：python2/python3
- 系统： Windows/Linux/macOS

## 3.设置cookie和user_id
打开weibospider文件夹下的"**weibospider.py**"文件，将"**your cookie**"替换成爬虫微博的cookie，后面会详细讲解如何获取cookie；将**user_id**替换成想要爬取的微博的user_id，后面会详细讲解如何获取user_id;
## 4.运行脚本
大家可以根据自己的运行环境选择运行方式，Linux可以通过
```bash
$ python weibospider.py
```
# 注意事项
1.user_id不能为爬虫微博的user_id。因为要爬微博信息，必须先登录到某个微博账号，此账号我们姑且称为爬虫微博。爬虫微博访问自己的页面和访问其他用户的页面，得到的网页格式不同，所以无法爬取自己的微博信息；<br>
2.cookie有期限限制，超过有效期需重新更新cookie。
