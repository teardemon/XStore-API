
# 发布Android应用的流程

Android发布一个应用的完整流程应该如下图所示：

![](http://7x00aw.com1.z0.glb.clouddn.com/publishing_preparing.png)

向用户发布一个完整的应用需要使用Release模式打包一个apk，跟debug模式的差异性主要在于release会使用你自己的keystore为apk包签名并且会使用zipalign工具优化apk包【关于zipalign工具的使用请我写的另外一篇[文章]()】。

如果你使用的是Android Studio和Gradle的话，通常签名和优化任务在你开发应用的过程中都将会是非常便捷的。在build.gradle文件中，可以配置上述签名、优化的过程。【你也许需要在我的blog中搜索关于Gradle构建系统的文章】


### End-user License Agreement

此为图中的EULA，直译过来是最终用户许可协议，它的价值在于可以帮助保护你个人、组织的一些权利，建议所有的应用都要具备一个用户最终许可协议。

### 关闭logging和debugging

在你构建应用之前请先确保以下事情：

- 请先将代码中关于Log的代码移除

- 在manifest文件中的application标签中将android:debuggable属性设置为false

- 删除工程目录下任何由log或者静态测试产生的文件

- 如果代码中使用了webview，请注意使用WebView.setWebContentsDebuggingEnabled()方法。

### 清理工程目录

- 尽量将文件按照标准的工程目录组织构建【[标准工程目录](http://developer.android.com/tools/projects/index.html#ApplicationProjects)天朝民众要墙墙墙】

- 关注你的jni/、src/、lib/目录，jni目录下只应该包含关于Android NDK的源码文件，像c、cpp、h或者mk文件，lib目录下只应该包含预先构建好的第三方库，像.so文件等。src目录下应该只包含java文件或者aidl文件，注意不要将jar文件包含进去。

- 删除res目录下不用的layout、drawable文件

- 删除lib目录下不使用的lib文件

- 更新res/raw目录和asset目录


