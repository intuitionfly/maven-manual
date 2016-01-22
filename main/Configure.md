# 配置 Apache Maven
对于Maven本身和项目构建的配置存在于不同的地方：

* `MAVEN_OPTS` 环境变量:

这个变量包含用于启动JPM运行Maven的参数，并且可以用来对Maven提供全局性的额外选项。 例如，JVM内存设置可以用`-Xms256m -Xmx512m`来定义。

* `settings.xml` 文件:

位于`USER_HOME/.m2`的配置文件用来保存Maven跨项目的配置。

* `.mvn` 目录:

位于项目顶层目录，文件`maven.config` 和 `extensions.xml` 包含运行Maven时项目指定的配置。

下面的向导包含了对于特定方面配置的更多信息：

* [Recommended Best Practice - Using a Repository Manager](http://maven.apache.org/repository-management.html)
* [Documentation for settings.xml](http://maven.apache.org/settings.html)
* [Configuring a HTTP Proxy](http://maven.apache.org/guides/mini/guide-proxies.html)
* [Configuring a repository mirror](http://maven.apache.org/guides/mini/guide-mirror-settings.html)
* [Various Tips for Configuring Maven](http://maven.apache.org/guides/mini/guide-configuring-maven.html)
* [Password Encryption](http://maven.apache.org/guides/mini/guide-encryption.html)