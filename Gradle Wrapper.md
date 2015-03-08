# Gradle Wrapper

Gradle Wrapper是一种官方推荐的使用Gradle的方式。它在windows上通常是一种批处理执行的脚本(.bat)在其他系统上是shell脚本。当你使用wrapper来启动gradle build时，它会自动下载Gradle并执行build任务，这也意味着可以将wrapper和工程一起分发给别人，别人无需预先装有gradle。

## 如何构建Wrapper

非常简单，你只需要在原有工程的build gradle中添加并配置wrapper task，然后再执行这个wrapper task即可。如下图所示：
build.gradle

```
task wrapper(type:Wrapper){
	gradleVersion	 = '2.0'
}
```

当执行完上述task后，整个工程的目录下会增加如下的文件

```
simple/
	gradlew
	gradlew.bat
	gradle/wrapper/
		gradle-wrapper.jar
		gradle-wrapper.properties
```
这些文件一定要添加到工程的版本控制系统中，只需要配置执行一次这个wrapper task就好了。这样的话，这个工程目录下增加了一个命令：gradlew，它的使用方式跟gradle是一样的

## 配置wrapper
你可以在wrapper task中定义你想使用的Gradle版本，在正式使用的时候，gradlew会从Gradle repository中下载最接近的版本。
如果你不想在使用gradlew时下载gradle，那么可以在工程目录下添加Gradle对应版本的zip包，当然了你可以在工程目录下的其他位置添加，只不过要在gradle-wrapper.properties文件中配置相对路径。

## *NIX系统文件权限配置

由于gradlew执行的操作设置到文件操作，在*NIX系统中受文件权限控制，所以为了使gradlew获取正常的文件操作权限，请执行命令

```
sh gradlew
```