# ipadis
自建IPA分发




##### 编写前端页面进行分发
我们有两种方式

1. 我们在网页的head标签中加入JS代码，当用户访问网页的时候自动触发，进行下载。

<script>
var url = "https://raw.githubusercontent.com/angryapes/ipadis/master/manifest.plist";
window.location = "itms-services://?action=download-manifest&url=" + url;
</script>
第2种：
打造一个炫酷的页面（此处省略），以web链接的形式当用户点击触发a标签的时候进行下载

<a href="itms-services://?action=download-manifest&url=https://raw.githubusercontent.com/angryapes/ipadis/master/manifest.plist">点击下载</a>
