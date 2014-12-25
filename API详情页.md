# API详情页

## gameDownload

### <font color="brown">功能</font>

提供游戏下载功能，支持断点续传。

### <font color="brown">URL示例</font>

http://api_host/version/gameDownload?gameId=12394

### <font color="brown">HTTP请求方式</font>

**GET**

### <font color="brown">请求参数</font>

参数名称|是否必须|传递方式|作用|
-------|------|-----|----|
gameId|<font color="red">是<font>|query|标示游戏，全局唯一|
Range| 否|header|断点续传请求部分，如果加入HTTP请求首部中，则按照HTTP 协议标准返回剩余的字节流。请求样式：Range:bytes=XXX-
### <font color="brown">返回结果</font>


### <font color="brown">返回字段说明</font>


### <font color="brown">其他</font>





