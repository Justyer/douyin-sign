# 一、AS、MAS签名版本 
## 抖音签名服务

Tiktik[抖音国外版] service demo is here [https://github.com/CrawlData/tiktok-sign](https://github.com/CrawlData/tiktok-sign)

这里演示抖音签名服务，如何生成新版的as、mas签名字段。每个接口可测试20次，如需更多使用，请发邮件到：**hello@crawldata.app**

```
curl --request POST \
  --url http://crawldata.app/api/douyin/v2/sign \
  --header 'Content-Type: application/json' \
  --data '{"url":"https://api.amemv.com/aweme/v1/aweme/post/?user_id=83774364341&max_cursor=0&count=20&source=video_search&app_type=normal&manifest_version_code=201&_rticket=1540307722505&ac=wifi&device_id=52650937206&iid=47182912991&os_version=8.1.0&channel=wandoujia&version_code=201&device_type=ONEPLUS%20A5000&language=zh&uuid=866265035315870&resolution=1080*1920&openudid=4617150637217100&update_version_code=2003&app_name=aweme&version_name=2.0.1&os_api=27&device_brand=OnePlus&ssmix=a&device_platform=android&dpi=420&aid=1128"}'
```

# 二、AS、CP签名版本
## 关于抖音签名协议

+ douyin-sign 是使用GO写的基于抖音Android客户端的接口签名算法，[视频演示](http://yxshare.oss-cn-hangzhou.aliyuncs.com/flyoffline/%E6%8A%96%E9%9F%B3%E8%A7%86%E9%A2%91%E6%BC%94%E7%A4%BA.mp4)

+ 有问题可以加我QQ：2633757493

+ 不想了解算法或者看不懂GO代码的朋友可以使用[douyin-demo](https://github.com/sweet8-asia/douyin-demo)


>首先[这里有一篇关于Android逆向工程的文章](http://www.520monkey.com/archives/1081)，反编译了抖音的libuserinfo.so文件的种种加密入口限制，使得自己的Android程序可以调用该so文件直接加密校验。这样的效果就是无需真正意义破解加密算法。

>我这里直接讲抖音的加密算法本身。火山小视频也一样。

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




