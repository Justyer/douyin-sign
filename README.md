## 概述
抖音版本更新非常快，但是实际使用的签名算法主要分为两种：

1. as和cp，2.0前的app版本使用，当前该算法仍然可用
2. as和mas，2.0后的app版本使用，当前app版本已更新到3.2.1，仍使用该算法

## 国际版算法
Tiktik/Musical.ly service is here: [https://github.com/CrawlData/tiktok-sign](https://github.com/CrawlData/tiktok-sign)

## 抖音算法演示
所有接口只能测试20次，更多请加QQ：**2633757493**，并描述清晰您的用途。

```
以下所有请求基于，所有链接可点击测试：
https://crawldata.app/api/douyin
```

| | as、cp版本  | as、mas版本 |
| ------------- | ------------- | ------------- |
| 首页动态  | [/v2/feed](https://crawldata.app/api/douyin/v2/feed)  | [/v1/feed](https://crawldata.app/api/douyin/v1/feed)  |
| 视频列表  | [/v2/aweme/post?user_id=83774364341](https://crawldata.app/api/douyin/v2/aweme/post?user_id=83774364341&max_cursor=0&count=20)  | [/v1/aweme/post?user_id=83774364341](https://crawldata.app/api/douyin/v1/aweme/post?user_id=83774364341&max_cursor=0&count=20)  |
| 喜欢列表  | [/v2/aweme/favorite?user_id=83774364341](https://crawldata.app/api/douyin/v2/aweme/favorite?user_id=83774364341&max_cursor=0&count=20)  | [/v1/aweme/favorite?user_id=83774364341](https://crawldata.app/api/douyin/v1/aweme/favorite?user_id=83774364341&max_cursor=0&count=20)  |
| 个人信息  | [/v2/user?user_id=83774364341](https://crawldata.app/api/douyin/v1/user?user_id=83774364341)  | [/v1/user?user_id=83774364341](https://crawldata.app/api/douyin/v1/user?user_id=83774364341)|
| 关注列表  | [/v2/user/following/list?user_id=83774364341&max_time=1541202996](https://crawldata.app/api/douyin/v2/user/following/list?user_id=83774364341&max_time=1541202996)  | [/v1/user/following/list?user_id=83774364341](https://crawldata.app/api/douyin/v1/user/following/list?user_id=83774364341&max_time=1541202996)  |
| 粉丝列表  | [/v2/user/follower/list?user_id=83774364341&max_time=1541473941](https://crawldata.app/api/douyin/v2/user/follower/list?user_id=83774364341&max_time=1541473941)  | [/v1/user/follower/list?user_id=83774364341](https://crawldata.app/api/douyin/v1/user/follower/list?user_id=83774364341&max_time=1541473941)  |
| 视频评论  | [/v2/comment/list?aweme_id=6615981222587796743](https://crawldata.app/api/douyin/v2/comment/list?aweme_id=6615981222587796743&cursor=0)  | [/v1/comment/list?aweme_id=6615981222587796743](https://crawldata.app/api/douyin/v1/comment/list?aweme_id=6615981222587796743&cursor=0)  |
| 商品橱窗  | [/v2/user/promotions?user_id=93712507975](https://crawldata.app/api/douyin/v2/user/promotions?user_id=93712507975&cursor=0)  |   |
| 直播列表  | [/v2/room/feed?cursor=0](https://crawldata.app/api/douyin/v2/room/feed?cursor=0)  |   |



> **[抖音国外版] Tiktik/Musical.ly service demo is here [https://github.com/CrawlData/tiktok-sign](https://github.com/CrawlData/tiktok-sign)**


>任何接口只能测试20次，更多请加QQ：**2633757493**，并描述清晰您的用途。

## 一、AS、MAS签名版本【最新版】
2.0后，采用as、mas签名，cp字段实际测试发现无效。
10月9日测试最新版**3.2.1**有效。
当前测试3.2.1可正常使用。
## 关键算法演示
#### 1、生成as、mas签名
```
curl -X "POST" "https://crawldata.app/api/douyin/v2/sign" \
     -H 'Content-Type: application/json' \
     --insecure \
     -d $'{
  "url": "https://aweme.snssdk.com/aweme/v1/feed/?type=0&max_cursor=0&min_cursor=-1&count=6&volume=0.3333333333333333&pull_type=2&need_relieve_aweme=0&filter_warn=0&req_from&is_cold_start=0&js_sdk_version=1.2.2&app_type=normal&manifest_version_code=321&_rticket=1541682949911&ac=wifi&device_id=59121099964&iid=50416179430&os_version=8.1.0&channel=gray_3306&version_code=330&device_type=ONEPLUS%20A5000&language=zh&vid=C2DD3A72-18E8-490e-B58A-86AD20BB8035&resolution=1080*1920&openudid=27b34f50ff0ba8e26c5747b59bd6d160fbdff384&update_version_code=3216&app_name=aweme&version_name=3.3.0&os_api=27&device_brand=OnePlus&ssmix=a&device_platform=android&dpi=420&aid=1128"
}'
```

#### 2、生成新的设备信息
[https://crawldata.app/api/douyin/v2/device/gen](https://crawldata.app/api/douyin/v2/device/gen)

## 实例接口演示

返回值中的vid等同于uuid。设备算法同时适用于android和ios

#### 1、首页动态流

[https://crawldata.app/api/douyin/v2/feed](https://crawldata.app/api/douyin/v2/feed)

#### 2、某人的视频列表

[https://crawldata.app/api/douyin/v2/aweme/post?user_id=83774364341&max_cursor=0&count=20
](https://crawldata.app/api/douyin/v2/aweme/post?user_id=83774364341&max_cursor=0&count=20)

#### 3、某人的喜欢列表

[https://crawldata.app/api/douyin/v2/aweme/favorite?user_id=83774364341&max_cursor=0&count=20
](https://crawldata.app/api/douyin/v2/aweme/favorite?user_id=83774364341&max_cursor=0&count=20)

#### 4、某人的个人信息

[https://crawldata.app/api/douyin/v2/user?user_id=83774364341](https://crawldata.app/api/douyin/v1/user?user_id=83774364341)

#### 5、某人关注的人列表

[https://crawldata.app/api/douyin/v2/user/following/list?user_id=83774364341&max_time=1541202996](https://crawldata.app/api/douyin/v2/user/following/list?user_id=83774364341&max_time=1541202996)

第一页max_time为当前时间轴，下一页通过上一页的返回数据获取新的max_time

#### 6、某人的粉丝列表

[https://crawldata.app/api/douyin/v2/user/follower/list?user_id=83774364341&max_time=1541473941](https://crawldata.app/api/douyin/v2/user/follower/list?user_id=83774364341&max_time=1541473941)

第一页max_time为当前时间轴，下一页通过上一页的返回数据获取新的max_time

#### 7、某个视频的评论

[https://crawldata.app/api/douyin/v2/comment/list?aweme_id=6615981222587796743&cursor=0](https://crawldata.app/api/douyin/v2/comment/list?aweme_id=6615981222587796743&cursor=0)

#### 8、某人的商品橱窗

[https://crawldata.app/api/douyin/v2/user/promotions?user_id=93712507975&cursor=0](https://crawldata.app/api/douyin/v2/user/promotions?user_id=93712507975&cursor=0)

#### 9、直播房间列表

[https://crawldata.app/api/douyin/v2/room/feed?cursor=0](https://crawldata.app/api/douyin/v2/room/feed?cursor=0)

第二页cursor传递1，以此类推

## 二、AS、CP签名版本【2.0前旧版】
2.0前的签名算法，可用于数据抓取。签名算法代码在[main.go](https://github.com/CrawlData/douyin-sign/blob/master/main.go)文件中，但是关键字段被隐藏，需要请联系我，qq：2633757493
#### 1、首页动态流

[https://crawldata.app/api/douyin/v1/feed](https://crawldata.app/api/douyin/v1/feed)

#### 2、某人的视频列表

[https://crawldata.app/api/douyin/v1/aweme/post?user_id=83774364341&max_cursor=0&count=20
](https://crawldata.app/api/douyin/v1/aweme/post?user_id=83774364341&max_cursor=0&count=20)

#### 3、某人的喜欢列表

[https://crawldata.app/api/douyin/v1/aweme/favorite?user_id=83774364341&max_cursor=0&count=20
](https://crawldata.app/api/douyin/v1/aweme/favorite?user_id=83774364341&max_cursor=0&count=20)

#### 4、某人的个人信息

[https://crawldata.app/api/douyin/v1/user?user_id=83774364341](https://crawldata.app/api/douyin/v1/user?user_id=83774364341)

#### 5、某人关注的人列表

[https://crawldata.app/api/douyin/v1/user/following/list?user_id=83774364341&max_time=1541202996](https://crawldata.app/api/douyin/v1/user/following/list?user_id=83774364341&max_time=1541202996)

第一页max_time为当前时间轴，下一页通过上一页的返回数据获取新的max_time

#### 6、某人的粉丝列表

[https://crawldata.app/api/douyin/v1/user/follower/list?user_id=83774364341&max_time=1541473941](https://crawldata.app/api/douyin/v1/user/follower/list?user_id=83774364341&max_time=1541473941)

第一页max_time为当前时间轴，下一页通过上一页的返回数据获取新的max_time

#### 7、某个视频的评论

[https://crawldata.app/api/douyin/v1/comment/list?aweme_id=6615981222587796743&cursor=0](https://crawldata.app/api/douyin/v1/comment/list?aweme_id=6615981222587796743&cursor=0)


# 三、抖音签名协议逆向过程

[这里有一篇关于Android逆向工程的文章](http://www.520monkey.com/archives/1081)，反编译了抖音的libuserinfo.so文件的种种加密入口限制，使得自己的Android程序可以调用该so文件直接加密校验。这样的效果就是无需真正意义破解加密算法。我这里直接以as、cp版本的协议讲解加密算法本身。火山小视频也一样。

### 抖音核心的步骤是：

+ 在查询串插入一个固定的键rstr
+ 对查询串进行按键排序并取值，对空格和+进行转义为a
+ 然后取MD5；如果时间轴&1为1，那么取多一次MD5
+ 将MD5结果分别和5******6、1******4进行2次错位排序算法
+ 将4的结果再进行一次错位排序，得到36位字符
+ 将字符分别取18位给到as和cp字段，追加到查询串最后

>在最新的SDK版本有了新的mas字段辅助校验，这个完全可以忽略，只要把查询串的version_code设置到169之前就可以跳过这个字段了。
另外aid为必填字段，其他和接口本身无关的字段都可去掉。
>由于这里涉及到抖音公司的核心利益，就不放具体代码和关键Key值了

![截图1](http://yxshare.oss-cn-hangzhou.aliyuncs.com/Screen%20Shot%202018-05-21%20at%2022.04.56.png)
![截图1](http://yxshare.oss-cn-hangzhou.aliyuncs.com/Screen%20Shot%202018-05-21%20at%2022.05.07.png)

> 以上演示的是as、cp版本的算法加密过程。
> 我的QQ是:2633757493




