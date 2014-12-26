# API详情页

## gameInfo

### <font color="brown">功能</font>

游戏详情页面内容展示API，需要提供icon、screenshot等多种信息

### <font color="brown">URL示例</font>

http://api_host/version/gameInfo?gameId=12394

### <font color="brown">HTTP请求方式</font>

**GET**

### <font color="brown">请求参数</font>

参数名称|是否必须|传递方式|作用|
-------|------|-----|----|
gameId|<font color="red">是<font>|query|标示游戏，全局唯一|
oldAppVersion|否|query|如果有老APP版本，提交此号，方便确定是否需要更新|
### <font color="brown">返回结果</font>

返回内容类型为application/json，示例如下：
<pre class="wiki">
{
  "status": 200,
  "msg": "获取成功",
  "data": {
    "app": {
      "addTime": 0,
      "apkSize": 20785659,
      "appendSize": 0,
      "categoryId": "2,0",
      "changeLog": "【新版特性】\r\n- 热聊，汇聚身边好玩的人和事\r\n- 巧遇附近心动的人，开启“爆灯”模式\r\n- 随时漫游各地，穿越世界交朋友\r\n- 语音通话彩铃，从此打破单一\r\n- 收藏也可再编辑，精彩内容随心更改\r\n\r\n【想怎么聊，就怎么聊】\r\n- 全新界面：化繁为简的架构，更加轻便自如，冰川蓝主题带来灵动清爽的视觉体验。\r\n- 语音通话：支持2人语音通话、3人语音通话、一群人语音通话都高清流畅，快拉上小伙伴体验下，想聊多久聊多久哦！\r\n- 视频聊天：可轻松开启视频通话，讨论组内快速多人视频，聊视频才能show出真相嘛！\r\n- 文件传输：与手机、电脑等多种终端进行文件传输。传文件、文件近传、我的收藏等多种传输方式，很强大有木有！\r\n- 移动支付：轻松进行手机充值、团购、电影票等操作。学会用“吃喝玩乐”，妈妈再也不用担心我的生活啦！\r\n- 空间动态：手机查看好友空间动态，分享个人精彩时刻。分享的不是寂寞，是生活！\r\n- 游戏中心：集合天天系列、全民系列等多款腾讯热门游戏。手机QQ玩游戏，根本停不下来！\r\n- 个性装扮：个性主题、名片、语音通话彩铃、气泡与头像挂件任你装扮。装扮的不是QQ，是格调！",
      "developerId": 371,
      "diffFileSize": 0,
      "displayName": "QQ",
      "favorite": false,
      "fitness": 0,
      "icon": "HTTP0",
      "id": 1359,
      "introduction": "QQ 致力于打造欢乐无限的沟通、娱乐与生活体验——乐在沟通15年，聊天欢乐8亿人！",
      "isFavorite": false,
      "keyWords": "QQ",
      "level1CategoryId": 2,
      "level1CategoryName": "聊天与社交",
      "level2CategoryId": 0,
      "packageName": "com.tencent.mobileqq",
      "publisherName": "深圳市腾讯计算机系统有限公司",
      "ratingScore": 2.5,
      "ratingTotalCount": 125701,
      "screenshot": "HTTP1,HTTP2,HTTP3,HTTP4",
      "source": "",
      "suitableType": 0,
      "updateTime": 1418875815874,
      "versionCode": 196,
      "versionName": "5.3.1"
    }
  }
}
</pre>


### <font color="brown">返回字段说明</font>

字段名称|作用|
-------|----|
versionCode|用来标示APP版本号|


### <font color="brown">其他</font>





