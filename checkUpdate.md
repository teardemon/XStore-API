# API详情页

## checkUpdate

### <font color="brown">功能</font>

检查APP更新接口

### <font color="brown">URL示例</font>

http://api_host/version/checkUpdate?appVersion=101

### <font color="brown">HTTP请求方式</font>

**GET**

### <font color="brown">请求参数</font>

参数名称|是否必须|传递方式|作用|
-------|------|-----|----|
appVersion|是|query|当传递此值，判断是否需要升级|

### <font color="brown">返回结果</font>

返回内容类型为application/json，示例如下：
<pre class="wiki">
{
  "status":200,
  "msg":"获取成功",
  "data":{
    "isNeedUpdate":true,
    "updateAddr":"http://XXXX/",
    "updateDescription":"XXXXXX"
  }
}
</pre>


### <font color="brown">返回字段说明</font>

字段名称|作用|
-------|----|
isNeedUpdate|是否需要强制更新|
updateAddr|更新地址|
updateDescription|更新内容|

### <font color="brown">其他</font>





