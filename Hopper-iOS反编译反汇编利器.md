# Hopper-iOS反编译反汇编利器

提起iOS的逆向工具，除了常见的Reveal、class-dump、Cycript等等，还有强大的静态分析软件-IDA Pro，但这款软件价格昂贵，就算是盗版也非常难找合适的mac版，对于不懂或者不熟练汇编语言的人来说，没有F5/F4插件那就是一种痛苦。但是现在福利来了，那就是Hopper，一款丝毫不逊色于IDA Pro的静态分析工具。因为网上也没有找到合适的教程，以下经验纯属自己瞎摸索出来的，如果不正确的话还请指正。【以逆向一款iOSAPP为例】

## 导入文件
首先你得有个解密过的App二进制文件【至于如何获得解密过的App二进制文件网上教程一堆堆，在这里就不赘述了】
点击菜单栏中File/Read Executable to Disassemble,放入二进制文件【App的二进制文件格式为MachO】