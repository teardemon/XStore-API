# **API Guide 商城API手册**
######_Made by **[MarkDown Extended](http://daringfireball.net/projects/markdown/syntax)**_ 

## 目录

1. [_移动应用API设计参考的原则_](#base)

2. [API基本结构、约定及基础规则]()

 - [API基本设计与约定](#API基本设计与约定)

 - [API请求基础规则](wiki://)
 
 - [API访问常量](wiki://)
 
 - [API响应基础规则](wiki://)
 

 
3. [API详细访问目录](wiki://)

4. [API的Q&A](wiki://)

5. [API修改回溯](wiki://)



###### 与产品经理商定是否需要添加其他更高级的API手册需求

## <a name="base">移动应用API设计参考的原则</a>

- API版本控制

- 与Web共用底层  

- 具有快速扩展的特性

- 减少客户端逻辑处理

-  是否需要建立iOS审核版专用API 

-  不冗余

-  完备

## API基本结构、约定及基础规则

### API基本设计与约定

一个标准的访问接口组成如下：**http://api\_host/version/ function_group/method**

<pre class="wiki">
各部分解释如下：

  - api_host :接口接入点地址
  
  - version : 接口访问版本
  
  - function_group : 函数集，一般以某个大功能/页面命名，如搜索（search）、个人信
  息（user）
  
  - method : 具体执行的方法 

</pre>
   

##### **其他约定** ： URL参数访问标准严格按照 [RFC 1738](http://tools.ietf.org/html/rfc1738)

API涉及的请求方法：**GET**、**POST**、**DELETE**，**传递参数的值均被URL编码**

### API请求基础规则

API涉及的传参方式：

传递参数的方式 | 备注 | 约定的缩写方式|示例|
-------------|----|------------|-----|
HTTP首部 |在HTTP的Header中添加Key:Value形式的参数，具体API指定Key与Value值|header|在HTTP header中，设置APPKey：<pre>...<br>XStoreKey:XXXXX<br>...</pre>|
URL Query|在HTTP GET请求中以连接字符串传递，?后连接请求字符串，传递参数间以&分割；?key1=value1&key2=value2|query|假设传递参数变量名为A，B，其值为C，D<pre>GET http://api.xstore.com/v1/test?A=C&B=D</pre>|
HTTP正文|在HTTP实体中传输，在头部中指定Content-type。除非特殊说明，默认是application/x-www-form-urlencoded|content|POST传递种类太多，只举出常用的例子：<br>json传参<pre>POST http://api.xstore.com/v1/test<br>Content-Type:application/json<br><br>{"A":"C","B":"D"}</pre><br>表单式传参<pre>POST http://api.xstore.com/v1/test<br>Content-Type:application/x-www-form-urlencoded<br><br>A=C&B=D</pre>|

### API访问常量
在API详细文档中涉及"是否需要用户登录"、"是否传递用户信息"等等诸如涉及标示用户的，我们采取**header**的方式传递用户的token；涉及区分客户端访问来源，我们采取**header**的方式传递客户端的id。具体如下

常量名称|值|作用|使用方法|
-----|----|----|----|
XStoreAPPID|Android:"XXXXXXXXXXXXXXXXXXXX"<br>iOS:"XXXXXXXXXXXXXXXXXXXXX"|标示客户端Android\\iOS，XStore是商城名|header方式使用，每个请求都要传递|
XStoreUserToken|这个需要登录API赋予|标示用户|header方式使用，根据API实际需要添加|
StaticAPI|XXXXXXXXXXXXXXXXX|向其请求api\_version和api\_host|客户端每次开启时|

### API响应基础规则

API响应无特殊说明，均为application/json。返回的基本样式
<pre>
{
  "status": 200,
  "msg": "成功",
  "data": {
    "A": "C",
    "B": {
      " D": "E"
    }
  }
}
</pre>

约定如下：

**字段名称**|**字段值**|**字段作用**|
-----------|---------|----------|
status|200/400|表示该次请求是否成功，区别于HTTP Code，指业务逻辑上的成功与否|
msg|请求成功/请求失败的具体原因|用来具体描述status所对应的含义
data|XXXXXX|返回的具体数据

