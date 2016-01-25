# Apache Maven 与 IDE 集成
所有流行的Java平台开发环境都直接支持Maven的许多功能。下面按字母顺序列出了流行的IDE：

## Eclipse IDE - M2Eclipse
[M2Eclipse](http://www.eclipse.org/m2e/) 是一个为了把Maven集成到Eclipse IDE中的一个官方的Eclipse项目。

它的功能包括：

* 从Eclipse环境中进行Maven构建
* 基于Maven的pom.xml对Eclipse构建目录进行依赖管理。
* 不用安装到Maven仓库就可以解决Eclipse工作空间的Maven依赖。
* 从远程Maven仓库中自动下载需要的依赖和源代码。
* 用向导创建新的Maven项目，pom.xml，也可以对已有的项目启用Maven支持。
* 对远程Maven库中的依赖进行快速搜索。
* 在Java编辑器中通过类名或包名查找需要的依赖/JAR包来快速修复。
* 与其它Eclipse工具集成，例如：WTP, AJDT, Mylyn, Subclipse等。

当你在IDE中做任何改动时，M2E会与你的Maven项目动态整合。如果你修改了依赖，或者在POM M2E中修改了Maven插件的配置，将会在Eclipse工作空间中自动同步这些改变。

## JetBrains IntelliJ IDEA
Intelli IDEA 有一个[对Maven的丰富功能集成](https://www.jetbrains.com/idea/help/maven.html).

## Netbeans IDE
NetBeans从6.7版本开始包含了对Maven的完整集成，7.0+版本包含了对Maven 3的支持。你可以在IDE中打开任何Maven项目然后马上开始编码。

更多信息请参考：[NetBeans.org wiki](http://wiki.netbeans.org/Maven).