# 安装 Apache Maven

Apache Maven的安装是一个解压并把包含`mvn`命令的`bin`目录添加到`PATH`中的简单过程。

具体步骤：

* 确保 `JAVA_HOME` 环境变量已经被设置并指向你的 JDK 安装目录

* 解压Maven发行包

		unzip apache-maven-3.3.3-bin.zip
或者

		tar xzvf apache-maven-3.3.3-bin.tar.gz
也可以用你喜欢的解压工具。

把建好的`apache-maven-3.3.3`目录里的`bin`目录添加到 `PATH` 环境变量里。

在命令窗口中用 `mvn -v` 确认是否成功。 结果看起来像这样：

		Apache Maven 3.3.3 (7994120775791599e205a5524ec3e0dfe41d4a06; 2015-04-22T04:57:37-07:00)
		Maven home: /opt/apache-maven-3.3.3
		Java version: 1.8.0_45, vendor: Oracle Corporation
		Java home: /Library/Java/JavaVirtualMachines/jdk1.8.0_45.jdk/Contents/Home/jre
		Default locale: en_US, platform encoding: UTF-8
		OS name: "mac os x", version: "10.8.5", arch: "x86_64", family: "mac"
# Windows Tips
* 检查环境变量的值：

		echo %JAVA_HOME% 
		C:\Program Files\Java\jdk1.7.0_51
* 添加到 `PATH`: 添加解压的发行包的bin目录到你的用户PATH环境变量，打开系统属性（Win + Pause），选择“高级”选项卡，点“环境变量”按钮，然后在用户变量中添加或选择PATH变量，加入值`C:\Program Files\apache-maven-3.3.3\bin`。同样的对话框可以用来设置 `JAVA_HOME`指向你的JDK的路径，例如`C:\Program Files\Java\jdk1.7.0_51`

* 打开一个新的命令提示窗(Win + R 然后键入 `cmd`) 并运行 `mvn -v`来验证是否安装成功。

# 基于Unix的操作系统 (Linux, Solaris 和 Mac OS X) Tips
* 检查环境变量的值

		echo $JAVA_HOME
		/Library/Java/JavaVirtualMachines/jdk1.8.0_45.jdk/Contents/Home
* 添加到 `PATH`

		export PATH=/opt/apache-maven-3.3.9/bin:$PATH