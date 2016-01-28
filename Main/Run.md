# 运行 Apache Maven
运行Maven的方式如下：

		mvn [options] [<goal(s)>] [<phase(s)>]
所有可用的 options 被编写进了help中，你可以用以下命令查看：

		mvn -h
构建Maven项目的典型调用使用Maven生命周期阶段。例如：

		mvn package
生命周期的构建和它们的阶段依次是：

* clean - pre-clean, clean, post-clean
* default - validate, initialize, generate-sources, process-sources, generate-resources, process-resources, compile, process-classes, generate-test-sources, process-test-sources, generate-test-resources, process-test-resources, test-compile, process-test-classes, test, prepare-package, package, pre-integration-test, integration-test, post-integration-test, verify, install, deploy
* site - pre-site, site, post-site, site-deploy

项目生成所有打包输出和文档并部署到仓库管理器的全新构建可以这样做：

		mvn clean deploy site-deploy
仅仅创建包并安装到本地仓库以供其它项目使用可以这样做：

		mvn clean install
对于Maven项目来说，这是一个最普通的构建调用。

当并不用作项目而是其它用途时，你可能想调用Maven的某部分实现的特定任务 － 这叫做插件的目标，例如：

		mvn archetype:generate
或

		mvn checkstyle:check
有很多插件可以用，而且它们实现了许多不同的目标。

更多资源:

[Building a Project with Maven](http://maven.apache.org/run-maven/index.html)