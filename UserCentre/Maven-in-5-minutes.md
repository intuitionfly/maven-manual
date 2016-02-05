# 5分钟体验Maven

## 预备课程

你必须理解如何在你的电脑上安装软件。如果你不知道如何做，你可以请教你办公室的同事，学校里的同学或者花点钱请别人讲解一下。请不要把这种问题发到Maven的邮件列表。

## 安装
Maven是一个Java工具，所以你必须先安装[Java](http://www.oracle.com/technetwork/java/javase/downloads/index.html)。

首先，[下载Maven](http://maven.apache.org/download.html)并[按指导安装](http://maven.apache.org/download.html#Installation)。之后在终端或命令行窗口中运行：

		mvn --version
这会输出你安装的Maven版本，例如：

		Apache Maven 3.0.5 (r01de14724cdef164cd33c7c8c2fe155faf9602da; 2013-02-19 14:51:28+0100)
		Maven home: D:\apache-maven-3.0.5\bin\..
		Java version: 1.6.0_25, vendor: Sun Microsystems Inc.
		Java home: C:\Program Files\Java\jdk1.6.0_25\jre
		Default locale: nl_NL, platform encoding: Cp1252
		OS name: "windows 7", version: "6.1", arch: "amd64", family: "windows"

取决于你的网络设置，你可能还需要一些额外的配置。如果需要，你可以看[Maven配置向导](http://maven.apache.org/guides/mini/guide-configuring-maven.html)。

**如果你使用Windows,你需要看看[Windows预备课程](http://maven.apache.org/guides/getting-started/windows-prerequisites.html)来确定你是否已经在Windows上准备好运行Maven了。**

## 创建项目
你需要一个地方来放项目，创建一个目录并在命令行中转到那个目录。在命令行中，运行以下Maven目标：

		mvn archetype:generate \
			-DgroupId=com.mycompany.app\
			-DartifactId=my-app \
			-DarchetypeArtifactId=maven-archetype-quickstart \
			-DinteractiveMode=false

*如果你刚刚安装好Maven,第一次运行可能需要比较长的时间。这是因为Maven会下载最常使用的工件（插件JAR和其它文件）到你的本地仓库。在运行成功前你也可能需要运行很多次这个命令。因为在你下载完成前远程服务器可能会超时。别担心，问题总会解决的。*

你会发现generate目标创建了一个与给定artifactId相同名字的目录。进入这个目录。

		cd my-app

在这个目录下你会看到这样的标准项目结构。

		my-app
		|-- pom.xml
		`-- src
		    |-- main
		    |   `-- java
		    |       `-- com
		    |           `-- mycompany
		    |               `-- app
		    |                   `-- App.java
		    `-- test
		        `-- java
		            `-- com
		                `-- mycompany
		                    `-- app
		                        `-- AppTest.java
`src/main/java`目录包含了项目代码，`src/test/java`目录包含了测试代码，`pom.xml`文件就是项目的**项目对象模型**，也叫**POM**。

### POM

在Maven中，`pom.xml`文件是项目配置的核心。这个配置文件中包含了以你想要的方式构建项目所需要的大部分信息。POM信息量很大，可能会让你对它的复杂性感到有些泄气，但想要有效的使用它，你并不用理解其中所有的细节。这个项目的POM：

		<project xmlns="http://maven.apache.org/POM/4.0.0" 
			xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
			xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
								http://maven.apache.org/xsd/maven-4.0.0.xsd">
		  <modelVersion>4.0.0</modelVersion>
		 
		  <groupId>com.mycompany.app</groupId>
		  <artifactId>my-app</artifactId>
		  <version>1.0-SNAPSHOT</version>
		  <packaging>jar</packaging>
		 
		  <name>Maven Quick Start Archetype</name>
		  <url>http://maven.apache.org</url>
		 
		  <dependencies>
		    <dependency>
		      <groupId>junit</groupId>
		      <artifactId>junit</artifactId>
		      <version>4.8.2</version>
		      <scope>test</scope>
		    </dependency>
		  </dependencies>
		</project>

### 我们刚刚做了什么?

我们运行了一个Maven目标：archetype:generate，而且给这个目标传递了一些参数。前缀archetype是包含这个目标的[插件](http://maven.apache.org/plugins/index.html)。如果你熟悉ant，你可能认为这和任务很像。这个目标创建了一个简单的基于一个archetype的项目。现在只用说插件是一系列通用作用的目标集合就行了。例如jboss-maven-plugin，它的目标就是“处理许多jboss的东西”。

### 构建项目

		mvn package
命令行将会打印出很多动作信息，并以如下信息结束：

		 ...
		[INFO] ------------------------------------------------------------------------
		[INFO] BUILD SUCCESSFUL
		[INFO] ------------------------------------------------------------------------
		[INFO] Total time: 2 seconds
		[INFO] Finished at: Thu Jul 07 21:34:52 CEST 2011
		[INFO] Final Memory: 3M/6M
		[INFO] ------------------------------------------------------------------------

与我们先运行的命令（archetype:generate）不同，你可能注意到第二次我们只是简单的一个词-“package”。这不是一个目标，而是一个阶段。一个阶段是[构建生命周期](http://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)中的一个步骤，一系列有序阶段中的一个。当给定一个阶段时，Maven会顺序执行每个有序阶段，直到给定的这个阶段。例如，如果我们运行compile阶段，真正会被执行的阶段是：

1. validate
1. generate-sources
1. process-sources
1. generate-resources
1. process-resources
1. compile

你可以用这条命令来测试下新编译并打包好的JAR：

		java -cp target/my-app-1.0-SNAPSHOT.jar com.mycompany.app.App
这时将会打印出经典的：

		Hello World!

## 	运行Maven工具
### Maven 阶段

尽管很难有一个详尽的列表，但列出的这些就是大多数被执行的通用的默认生命周期阶段。

- **validate**: 验证项目正确性以及所有需要的信息都可用
- **compile**: 编译项目的源码
- **test**: 使用合适的单元测试框架测试编译好的源码。这些测试不应该要求代码被打包或部署。
- **package**: 取得编译好的代码并打包成一个可发布的格式，例如JAR
- **integration-test**: 处理并部署包到可以运行集成测试的环境中
- **verify**: 运行所有的检查条件来验证包的有效性并满足质量标准。
- **install**: 把包安装到本地仓库，用来给本地的其它项目提供依赖
- **deploy**: 在集成或发布环境中完成，复制最终的包到远程仓库，共享给其它开发人员或项目。

除了以上默认列表中的Maven生命周期，还有另外两个：

- **clean**: 清除之前构建中生成的工件
- **site**: 为项目生成站点文档

阶段实际上是映射到隐含的目标的。根据阶段执行的特定的目标是依赖于项目的打包类型的。例如，如果项目类型是JAR,那打包就会执行jar:jar，如果类型是WAR，会执行war:war。

有趣的是，阶段和目标是按给定顺序执行的。

		mvn clean dependency:copy-dependencies package
这条命令会清理项目，复制依赖，然后打包项目（根据包类型执行所有阶段）。

### 生成站点

		mvn site
这个阶段基于项目的POM生成一个站点。你可以在target/site里看到生成的文档。

## 结论
我们希望这个快速总览会激起你对Maven多样性的兴趣。注意这只是一个非常短小的快速上手向导。现在你已经准备好对你刚才做的有更细节的理解了。看看[Maven新手向导](http://maven.apache.org/guides/getting-started/index.html)吧。