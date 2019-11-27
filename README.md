# ipadis
自建IPA分发


##### 配置

问题：自建ipa的下载渠道，app更新过程中手机桌面显示两个相同的图标，完成后只剩一个图标
解决方案 :manifest.plist文件里面的bundle-identifier填写了重签名后的bundleId了，用打包时候的bundleId就不会出现两个图标了

下载安装应用，使用的是itms-services:协议
'itms-services://?action=download-manifest&url=https://plist文件的地址'


##### 编写前端页面进行分发

1. 我们在网页的head标签中加入JS代码，当用户访问网页的时候自动触发，进行下载。

'''javascript
<script>
var url = "https://raw.githubusercontent.com/angryapes/ipadis/master/manifest.plist";
window.location = "itms-services://?action=download-manifest&url=" + url;
</script>
'''

2. 打造一个炫酷的页面（此处省略），以web链接的形式当用户点击触发a标签的时候进行下载

'''
<a href="itms-services://?action=download-manifest&url=https://raw.githubusercontent.com/angryapes/ipadis/master/manifest.plist">点击下载</a>
'''

3. 如果通过ios应用内安装，代码大概如下所示
iOS:'[[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"itms-services://?action=download-manifest&url=https://plist文件的地址"]]'



##### 附应用测试发布平台
1. [fir.im](http://fir.im/)
2. [蒲公英](http://www.pgyer.com/)
3. [Pre.im](http://pre.testin.cn/)
4. [TestFlight](https://developer.apple.com/testflight/)
