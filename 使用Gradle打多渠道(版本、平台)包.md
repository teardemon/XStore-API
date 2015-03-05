# 使用Gradle打多渠道(版本、平台)包

首先是接下来几个关键的名词解释：
当然了，也许还需要参考我的别的文章:

[applicationID和packageName的差异]()


```
build variant: 顾名思义，也就是我们所谓的渠道包、平台包、版本包等等诸如此类的说法

product flavor: gradle 用来构建上述不同包的配置选项，一般包含applicationID、
flavorDimension应用所有者、versionCode、versionName等选项的配置

build type:这个主要是配置构建过程中需要进行的额外的操作配置，包含的选项有minifyEnable、signingConfig、zipAlignEnabled等等,它定义了两种release和debug

一个build variant=一个product flavor+一个build type

```

### 创建product variant概览

- 在build file文件中定义product flavor

- 为每个product flavor创建额外的源码目录（非必须）

- 为你的工程添加每个flavor独有的源码（非必须）


### 示例

先来描述需求：你有一个BuildSystemExample工程，你为此工程创建两个flavor：demo和full。所有flavors共用MainActivity，上面有一个按钮用来启动第二个页面：SecondActivity。这个新的Activity在不同flavor上是不同的。

#### 第一步 定义product flavor

```
...
android {
    ...
    defaultConfig { ... }
    signingConfigs { ... }
    buildTypes { ... }
    productFlavors {
        demo {
            applicationId "com.buildsystemexample.app.demo"
            versionName "1.0-demo"
        }
        full {
            applicationId "com.buildsystemexample.app.full"
            versionName "1.0-full"
        }
    }
}
...

```

在这个例子中defaultConfig配置了默认的关于应用的一些信息，在flavor中，我们将applicationId重写了默认值


### 第二步 为每个flavor添加额外的源码目录

在本例子中，这一步是必需的。

根据需求，我们在src/目录下新建一个demo目录，形成如下的目录

```
app/src/demo/java
app/src/demo/res
app/src/demo/res/layout
app/src/demo/res/values
```

### 第三步，为每个flavor添加特定代码、资源文件

在src/demo/java目录下新建同包名的package，并在此目录下添加特定flavor的特定activity源码，类似地在src/demo/res/layout和src/demo/res/values目录下添加特定资源文件。类似地，创建full的flvaor。


### buildTypes

前面我们只说了flavor，并没有提及到buildType，要知道variant=flvaor+build type的，下面是有关buildtype的配置

```
...
android {
    ...
    defaultConfig { ... }
    signingConfigs { ... }
    buildTypes { ... }
    productFlavors {...}
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        }
         debug {
            debuggable true
        }
    }
}
...
```

这样，实际上我们产生了4个build variant，分别是demodebug、demorelease、fulldebug、fullrelease

我们可以通过执行gradlew build完成4个variant一起打包，也可以执行gradlew assembledemoDebug来完成demoDebug这个variant的打包