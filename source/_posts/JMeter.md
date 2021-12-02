---
    title: 压力测试工具-JMeter # 文章标题  
    date: 2021/08/23 10:02:04
    tags:
    - 其他   https://zssaer.oss-cn-chengdu.aliyuncs.com
    categories: 其他 # 分类
    thumbnail: https://zssaer.oss-cn-chengdu.aliyuncs.com/joshua-sortino-LqKhnDzSF-8-unsplash.jpg?x-oss-process=style/wallpaper # 略缩图
---
<h1 align = "center">压力测试工具-JMeter</h1>

学习了Sentinel框架后，为了测试并发等功能，需要使用工具才行。

这儿简绍Apache JMeter -基于Java开发的压力测试工具。

![](https://zssaer.oss-cn-chengdu.aliyuncs.com/8ad4b31c8701a18bc4cdb31613c2b70e2938febd.jpeg)

进行Http多线程测试操作:

由于JMeter是基于JAVA编写,所以首先确保操作系统拥有JAVA运行环境才行。

前往官网下载JMeter：[http://jmeter.apache.org/download_jmeter.cgi](http://jmeter.apache.org/download_jmeter.cgi)，最新版本已经支持中文语言。

下载后解压，打开bin\ApacheJMeter.jar文件，运行JMeter。

![](https://zssaer.oss-cn-chengdu.aliyuncs.com/20210819172921.png)

在`测试计划`右击选择添加/线程/线程组

![](https://zssaer.oss-cn-chengdu.aliyuncs.com/20210819173126.png)

线程组右边的线程属性,线程数表示启动多少线程(相当于用户数量),Ramp-UP时间代表隔多长时间执行，0代表同时并发。而循环次数不言而喻就是反复循环测试次数。

设置好后再在`线程组`上右击添加/配置与元件/HTTP请求默认值,来进行配置每个HTTP请求的默认值。

![](https://zssaer.oss-cn-chengdu.aliyuncs.com/20210819173621.png)

之所以使用`HTTP请求的默认值`,就是为了方便大规模接口测试,可以先将Http地址确认下来。

然后再在`HTTP请求的默认值`中设置基本地址和端口:

![](https://zssaer.oss-cn-chengdu.aliyuncs.com/20210819173842.png)

设置好基本值后,然后再在`线程组`上右击选择添加/取样器/HTTP请求,设置测试请求。

![](https://zssaer.oss-cn-chengdu.aliyuncs.com/20210819174009.png)

设置其HTTP请求的需要测试的路径和请求方法。由于已经设置了HTTP请求的默认值,所以这儿的服务器IP\端口这些都不需要再次填写

![](https://zssaer.oss-cn-chengdu.aliyuncs.com/20210819174109.png)

在`HTTP请求`上右击,点击添加/断言/响应断言,来为该请求测试设置断言,来进行每次测试的判断,判断是否成功还是失败。

![](https://zssaer.oss-cn-chengdu.aliyuncs.com/20210819174353.png)

设置其断言判断,由于网页的请求采取Rest方式,不管是Json还是什么,都是以文本,所以这儿测试字段 设置为`响应文本`,然后再在选择判断条件,以及设置相关判断参数.

![](https://zssaer.oss-cn-chengdu.aliyuncs.com/20210819174543.png)

我们再在`线程组`上右击,点击监听器/察看结果树,来测试返回结果

![](https://zssaer.oss-cn-chengdu.aliyuncs.com/20210819174833.png)

好了,最后点击上方工具栏中的第一个绿色箭头 启动整个测试.最后在`察看结果树`便可以看见结果,由于我们对请求设置了断言,所以其中成功和失败一目了然:

![](https://zssaer.oss-cn-chengdu.aliyuncs.com/20210819175124.png)

这便是简易的JMeter的Http压力测试的方法教程。