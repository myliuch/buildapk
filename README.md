# 多渠道打包实现

### 说明
##### 大家都知道国内的应用市场很多，为了兼容每个市场做数据统计我们需要为不同的应用市场上的apk安装包设置不同的渠道号，每次发版的时候多则数百的渠道包需要打，每个渠道包都要经过编译，签名，打包等过程，大概一两分钟的时间，若是数百的渠道包，那么。。。。。
##### 程序员就是为了解决这种重复的无效的工作的群里，好在美团的工程师们找到了一种比较简洁的打包方式。
##### 如果能直接修改apk的渠道号，而不需要再重新签名能节省不少打包的时间。直接解压apk，解压后的根目录会有一个META-INF目录，如果在META-INF目录内添加空文件，可以不用重新签名应用。因此，通过为不同渠道的应用添加不同的空文件，可以唯一标识一个渠道。

##### 这里就是已这个思路实现的多渠道打包，经测试，没有发现兼容性问题，平均下来每个渠道包只需要花费两三秒的时间，大大提高了打包的效率。

### 使用说明
* 首先需要安装python环境，生成渠道包的脚本是python脚本，我这里安装的是python3.5，不知道如何安装的，请自行百度。。。
* 打包一个普通的apk，我们是在这个渠道包的基础上更改其内容，生成其他渠道包的。
* 运行apk.py脚本，脚本会扫描当前目录下的所有apk文件，然后生成outputDir文件夹以及不同的渠道包。

### 目录文件
* .apk文件是已经打好包的安装文件，我们是在这个apk文件基础上生成其他渠道包的。
* info文件夹下包含：channel.txt和empty.txt，channel.txt是渠道号的集合已回车分割，可参考自己的实际情况修改。
* outputDir文件夹是生成渠道包集合的文件夹。
