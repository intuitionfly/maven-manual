# Maven 初学者指南
这篇指南可以做为第一次使用Maven的参考，但同时也可以用作独立的参考和通用用例解决方案的手册。对于第一次使用Maven的用户，建议顺序阅读。对于已经比较熟悉Maven的用户，这篇指南也力图对一些常见的需求提供快速解决方案。现在我们假定你已经在电脑上下载并安装了Maven。如果你没有完成这一步，请参考[下载和安装](http://maven.apache.org/download.html)。

好了，你现在已经有了Maven并随时可以开始了。在我们开始看例子之前，我们将粗略讲讲什么是Maven，它能怎样在你的日常工作和与其它同事协作时帮助你。当然，Maven为小项目工作，但也通过让团队成员专注于项目需求而帮助团队更高效的运转。你可以把构建基础架构的工作交给Maven！

## 问题列表
* 什么是Maven？
* Maven如何惠及我的开发过程？
* 如何设置Maven?
* 如何开始我的第一个Maven项目？
* 如何编译我的程序源码？
* 如何编译我的测试源码并运行单元测试？
* 如何创建一个JAR包并放到我的本地仓库中？
* SNAPSHOT版本是什么？
* 如何使用插件？
* 如何添加资源到我的JAR包？
* 如何过滤资源文件？
* 如何使用外部依赖？
* 如何部署JAR包到远程仓库？
* 如何创建文档？
* 如何构建其它类型的项目？
* 如果一次构建多个项目？

### 什么是Maven？
第一眼看上去Maven会表现出很多东西，但扼要的说，Maven是在项目基础结构构建上应用模式的一个尝试，它通过采用最佳实践来提供一个清晰的路径，以便提升理解力和生产力。Maven是本质上是一个项目管理和综合工具，因些它提供了一种方法来帮助管理：
* 构建
* 编写文档
* 生成报表
* 依赖
* 源代码管理
* 版本发布
* 发行

如果您想知道Maven的更多背景信息，您可以了解Maven的[理念](http://maven.apache.org/background/philosophy-of-maven.html)和[历史](http://maven.apache.org/background/history-of-maven.html)。现在，让我们看看你能如何从使用Maven中受益。
### Maven如何惠及我的开发过程？
Maven可以通过使用标准的惯例和实践，加快开发周期，同时帮你达到更高的成功率，使你在构建过程中获益。

现在，我们已经介绍了一点点Maven的历史和宗旨。让我们来看看一些真实的例子来让你用Maven运行！
### 如何设置Maven?
Maven的默认设置通常已经足够了，但如果你需要更改缓存位置或者是配置HTTP代理服务器，你将需要创建配置项。有关详细信息，请参阅Maven配置指南。
### 如何开始我的第一个Maven项目？
我们现在就开始创建你的第一个Maven项目！要创建我们的第一个Maven项目，我们将使用Maven原型机制。一个原型被定义为相同种类的所有其它项目均采用的一个原始模式或模型。在Maven中，原型是一个项目模板，它基于一些用户输入来生成一个针对用户需求的可工作的Maven项目。我们将告诉你原型机制如何工作，但如果您想了解更多关于原型的信息，请参阅[原型介绍](http://maven.apache.org/guides/introduction/introduction-to-archetypes.html)。

现在创建第一个项目！为了创建最简单的Maven项目，在命令行中运行以下命令：

		mvn -B archetype:generate \
		-DarchetypeGroupId=org.apache.maven.archetypes \
		-DgroupId=com.mycompany.app \
		-DartifactId=my-app
一旦你执行了这条命令，你会发现发生了一些事。首先，你会发现一个名为`my-app`的目录已经创建，而且这个目录包含一个名为`pom.xml`的文件，内容看起来像这样：

		<project xmlns="http://maven.apache.org/POM/4.0.0"
		  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
		                      http://maven.apache.org/xsd/maven-4.0.0.xsd">
		  <modelVersion>4.0.0</modelVersion>
		  <groupId>com.mycompany.app</groupId>
		  <artifactId>my-app</artifactId>
		  <packaging>jar</packaging>
		  <version>1.0-SNAPSHOT</version>
		  <name>Maven Quick Start Archetype</name>
		  <url>http://maven.apache.org</url>
		  <dependencies>
		    <dependency>
		      <groupId>junit</groupId>
		      <artifactId>junit</artifactId>
		      <version>4.11</version>
		      <scope>test</scope>
		    </dependency>
		  </dependencies>
		</project>

`pom.xml`包含了这个项目的项目对象模型（POM）。在Maven中POM是基本工作单位。记住这很重要，因为Maven本质上是以项目为中心，所有东西都围绕着项目的理念。总之，POM包含了关于项目的所有重要信息，基本上可以一站式的找到关于项目的任何东西。理解POM是很重要的，新用户最好参考下[POM介绍](http://maven.apache.org/guides/introduction/introduction-to-the-pom.html)。

这是一个非常简单的POM，但仍然显示了每个POM所包含的关键信息，所以让我们看看它们，来熟悉下POM的要点：

* **project** 这是在所有pom.xml文件中最高层的元素
* **modelVersion** 这个元素指定了这个POM使用了哪个版本的对象模型。模型本身的版本并不会经常改变但却是必需的，这是为了在Maven开发者认为需要改变模型时保证使用的稳定性。
* **groupId** 这个元素指定了创建这个项目的组织或团队的唯一标识符。gourpId是项目的关键标识符之一，而且通常基于你的组织的完整有效的域名。例如`org.apache.maven.plugins`就是为所有Maven插件指定的groupId。
* **artifactId** 这个元素指定了这个项目生成的主要工件的唯一基本名。一个项目的主要工件通常是一个JAR文件。像代码包之类的次要工件也使用artifactId作为它们的最终名称的一部分。一个Maven生成的典型工件会有这样的形式：<artifactId\>-<version\>.<extension\> (例如, myapp-1.0.jar).
* **packaging** 这个元素指定了这个工件的打包类型(如 JAR, WAR, EAR, 等)。这不仅意味着工件会生成JAR, WAR, 或者 EAR，而且也指定了构建过程的一部分所使用的一个特定生命周期。(生命周期是我们会在这篇指南中深入讨论的一个话题。现在，只用记住项目指定的打包类型在定制构建的生命周期时会产生作用。) 这个元素的默认值是JAR，所以大多数项目不用特意指定。
* **version** 这个元素指定了项目生成的工件版本。Maven会在版本管理上长期帮助你，而且你将会在version中经常看到SNAPSHOT描述符，它指出这个项目正处于开发当中。我们将在这个指南中讨论Snapshot的用法和它们如何更有效。
* **name** 这个元素指定了项目显示的名称。它经常被用于Maven生成的文档。
* **url** 这个元素指定了哪里可以找到项目站点。它经常被用于Maven生成的文档。
* **description** 这个元素提供了项目的基本描述。它经常被用于Maven生成的文档。

一个关于POM中有哪些元素可用的完整参考可以参看[POM参考](http://maven.apache.org/ref/current/maven-model/maven.html)。让我们现在回到手上的这个项目。

第一个项目原型生成后，你会发现创建好的下面的目录结构：

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
可以看到，原型创建来的项目有一个POM，一个程序的源码树和一个测试的源码树。这是Maven项目的标准布局。（程序代码位于`${basedir}/src/main/java`,测试代码位于`${basedir}/src/test/java`，${basedir}就是包含`pom.xml`的目录。）

如果你想手动创建一个Maven项目，我们建议你使用这个目录结构。这是一个Maven约定，如果想了解更多，你可以阅读[标准目录布局的介绍](http://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html)。

现在我们有了一个POM，一些程序代码和一些测试代码，你可能会问……
### 如何编译我的程序源码？
改变路径到使用archetype:generate创建的pom.xml的目录，运行下面的命令编译你的程序代码：

		mvn compile
运行完这个命令，你应该看到如下输出：

		[INFO] ----------------------------------------------------------------------------
		[INFO] Building Maven Quick Start Archetype
		[INFO]    task-segment: [compile]
		[INFO] ----------------------------------------------------------------------------
		[INFO] artifact org.apache.maven.plugins:maven-resources-plugin: \
		  checking for updates from central
		...
		[INFO] artifact org.apache.maven.plugins:maven-compiler-plugin: \
		  checking for updates from central
		...
		[INFO] [resources:resources]
		...
		[INFO] [compiler:compile]
		Compiling 1 source file to <dir>/my-app/target/classes
		[INFO] ----------------------------------------------------------------------------
		[INFO] BUILD SUCCESSFUL
		[INFO] ----------------------------------------------------------------------------
		[INFO] Total time: 3 minutes 54 seconds
		[INFO] Finished at: Fri Sep 23 15:48:34 GMT-05:00 2005
		[INFO] Final Memory: 2M/6M
		[INFO] ----------------------------------------------------------------------------
你第一次运行这个命令（或其它命令）时，Maven需要下载所有的插件和关联的依赖来满足这条命令。在一个干净的Maven安装中，这会花掉好一会的时间（在上面的输出中，大概需要4分钟）。如果你再次运行这条命令，Maven已经有所需要东西，所以不用再下载，再次运行就会快得多。

输出里可以看到，编译好的class被放在`${basedir}/target/classes`，这是另一个标准Maven约定。所以如果你是一个敏锐的观察者，你会发现使用标准约定，上面的POM会非常小，并且你也不用明确的告诉Maven你的代码在哪或者应该输出到哪里。通过遵守标准Maven约定，你可以用很小的力气就完成很多东西。一个非正式的比较，让我们看看用[ant](http://ant.apache.org/)完成[同样的事](http://maven.apache.org/ant/build-a1.xml)你需要做哪些事。

现在，编译应用的程序代码这棵代码树很简单，并且Ant脚本看来和上面的POM差不多大小。但我们将会看到用那个简单的POM可以做的更多。

### 如何编译我的测试源码并运行单元测试？
现在你已经成功编译你的程序代码，并且现在你也有一些单元测试需要编译和执行（*因为每个程序员总会编写并执行它们的单元测试。* **呵呵**）

运行下面的命令：
		mvn test
通过执行这个命令你应该可以看到以下输出：

		[INFO] ----------------------------------------------------------------------------
		[INFO] Building Maven Quick Start Archetype
		[INFO]    task-segment: [test]
		[INFO] ----------------------------------------------------------------------------
		[INFO] artifact org.apache.maven.plugins:maven-surefire-plugin: \
		  checking for updates from central
		...
		[INFO] [resources:resources]
		[INFO] [compiler:compile]
		[INFO] Nothing to compile - all classes are up to date
		[INFO] [resources:testResources]
		[INFO] [compiler:testCompile]
		Compiling 1 source file to C:\Test\Maven2\test\my-app\target\test-classes
		...
		[INFO] [surefire:test]
		[INFO] Setting reports dir: C:\Test\Maven2\test\my-app\target/surefire-reports
		 
		-------------------------------------------------------
		 T E S T S
		-------------------------------------------------------
		[surefire] Running com.mycompany.app.AppTest
		[surefire] Tests run: 1, Failures: 0, Errors: 0, Time elapsed: 0 sec
		 
		Results :
		[surefire] Tests run: 1, Failures: 0, Errors: 0
		 
		[INFO] ----------------------------------------------------------------------------
		[INFO] BUILD SUCCESSFUL
		[INFO] ----------------------------------------------------------------------------
		[INFO] Total time: 15 seconds
		[INFO] Finished at: Thu Oct 06 08:12:17 MDT 2005
		[INFO] Final Memory: 2M/8M
		[INFO] ----------------------------------------------------------------------------

注意输出中的一些东西：

* Maven这次下载了更多的依赖。这些依赖和插件对运行测试是必需的（它已经有了编译需要的依赖，不会重复下载）。
* 在编译并执行测试前，Maven编译了main代码（所有这些类都是最新的因为我们从上次编译后并没有改任何东西。）

如果你只是想编译你的测试代码（但不运行测试），你可以执行下面这条命令：

		mvn test-compile
现在你可以编译你的应用程序代码，编译测试并执行测试，你想要继续下个逻辑步骤，所以你会问……

### 如何创建一个JAR包并放到我的本地仓库中？
制造一个JAR文件简单直接，它可以通过执行以下命令完成：

		mvn package
如果你看看工程的POM，你会注意到`packaging`元素被设置成了`jar`。这就是Maven如何从上面的命令中知道要去生成一个JAR文件（我们会在之后深入讲到）。你现在可以看看`${basedir}/target`目录，可以发现JAR文件已经生成好了。

现在你想要把工件生成的JAR文件安装到你的本地仓库中（默认位置`~/.m2/repository`）。关于仓库的更多信息你可以参考[仓库介绍](http://maven.apache.org/guides/introduction/introduction-to-repositories.html)，但现在先继续安装我们的工件！执行下面的命令：

		mvn install
执行这条命令应该可以看到下面的输出：

		[INFO] ----------------------------------------------------------------------------
		[INFO] Building Maven Quick Start Archetype
		[INFO]    task-segment: [install]
		[INFO] ----------------------------------------------------------------------------
		[INFO] [resources:resources]
		[INFO] [compiler:compile]
		Compiling 1 source file to <dir>/my-app/target/classes
		[INFO] [resources:testResources]
		[INFO] [compiler:testCompile]
		Compiling 1 source file to <dir>/my-app/target/test-classes
		[INFO] [surefire:test]
		[INFO] Setting reports dir: <dir>/my-app/target/surefire-reports
		 
		-------------------------------------------------------
		 T E S T S
		-------------------------------------------------------
		[surefire] Running com.mycompany.app.AppTest
		[surefire] Tests run: 1, Failures: 0, Errors: 0, Time elapsed: 0.001 sec
		 
		Results :
		[surefire] Tests run: 1, Failures: 0, Errors: 0
		 
		[INFO] [jar:jar]
		[INFO] Building jar: <dir>/my-app/target/my-app-1.0-SNAPSHOT.jar
		[INFO] [install:install]
		[INFO] Installing <dir>/my-app/target/my-app-1.0-SNAPSHOT.jar to \
		   <local-repository>/com/mycompany/app/my-app/1.0-SNAPSHOT/my-app-1.0-SNAPSHOT.jar
		[INFO] ----------------------------------------------------------------------------
		[INFO] BUILD SUCCESSFUL
		[INFO] ----------------------------------------------------------------------------
		[INFO] Total time: 5 seconds
		[INFO] Finished at: Tue Oct 04 13:20:32 GMT-05:00 2005
		[INFO] Final Memory: 3M/8M
		[INFO] ----------------------------------------------------------------------------

请注意（运行测试的）surefire插件会查找有特定命名约定的文件。测试默认包括：

* \*\*/*Test.java
* \*\*/Test*.java
* \*\*/*TestCase.java

默认排除：

* \*\*/Abstract*Test.java
* \*\*/Abstract*TestCase.java

你已经做过设置，构建，测试，打包，安装一个典型Maven项目的过程。大多数项目会用Maven做的东西都是相似的，而且如果你注意到，基于这点你能做的每件事都是被一个叫做POM的18行文件所驱动。如果你看一个提供了目前为止你做的相同功能的典型的Ant[构建文件](http://maven.apache.org/ant/build-a1.xml)，你会注意到它的大小已经是POM的2倍了，而我们才刚刚开始而已。POM不需要增加更多的东西，我们还可以用Maven完成更多的可用功能。而为了完成我们例子以外的更多功能，你必须在ant构建文件中添加内容，这是容易出错的。

所以你还可以免费获得什么其它东西？即使只是像我们上面这样简单的POM，仍然有大量的Maven插件马上就可以使用。我们在这里特别提到一个，因为它是Maven最赞的功能之一：你不用做任何其它工作，这个POM已经有足够的信息为你的工程生成一个Web站点！你可能非常想定制你的Maven站点，但如果你有时间上的压力，你只需要提供项目的基本的信息并执行下面的命令：

		mvn site
有大量其它独立目标也会被运行，例如：

		mvn clean
这将移除`target`目录连同之前构建的数据，现在干净了。

可能你想为工程生成IntelliJ IDEA的描述器？

		mvn idea:idea
这可以在之前的IDEA工程上运行——它会更新设置而不是重新创建。

如果你使用Eclipse IDE，只用运行：

		mvn eclipse:eclipse
**注意**：一些Maven 1.0里的熟悉目标还能用——例如`jar:jar`，但可能产生并不是你期望的行为。目前，`jar:jar`并不会重新编译码——它将会从`target/classes`目录简单的创建一个JAR，在这个假设下，所有其它的事已经被完成了。
### SNAPSHOT版本是什么？
注意`pom.xml`中version标记中的值有一个后缀：`-SNAPSHOT`。

		<project xmlns="http://maven.apache.org/POM/4.0.0"
		  ...
		  <groupId>...</groupId>
		  <artifactId>my-app</artifactId>
		  ...
		  <version>1.0-SNAPSHOT</version>
		  <name>Maven Quick Start Archetype</name>
		  ...

`SNAPSHOT`说明这是一个开发分支的‘最新’代码，不保证代码的稳定性和不变性。反之，一个‘发布’版本的代码（version中没有`SNAPSHOT`后缀）是不变的。

换句话说，`SNAPSHOT`版本是在最终‘发布’版本之前的‘开发’版本。它比‘发布’版本要老。

在[发布](http://maven.apache.org/plugins/maven-release-plugin/)过程中，版本**x.y-SNAPSHOT**改变为**x.y** 。发布过程同样把开发版本号增加成了**x.(y+1)-SNAPSHOT** 。例如版本**1.0-SNAPSHOT** 发布后版本为**1.0**，并且新的开发版本号为**1.1-SNAPSHOT** 。

### 如何使用插件？
无论何时你想要对Maven项目进行定制化构建，都可以通过添加或配置插件来完成。

**Maven 1.0用户注意**：在Maven 1.0中，你可以添加一些`preGoal`到`maven.xml`中，添加一些条目到`project.properties`中。但在这里是有点不同的。

举个例子，我们配置了Java编译器来允许JDK 5.0的代码。在POM中简单的加入：

		...
		<build>
		  <plugins>
		    <plugin>
		      <groupId>org.apache.maven.plugins</groupId>
		      <artifactId>maven-compiler-plugin</artifactId>
		      <version>3.3</version>
		      <configuration>
		        <source>1.5</source>
		        <target>1.5</target>
		      </configuration>
		    </plugin>
		  </plugins>
		</build>
		...

你会发现所有Maven插件看起来都像依赖－从某些方面看，它们确实是的。这些插件将会被自动下载并使用－如果需要，你可以指定一个特定版本（默认使用最新版本）。

`configuration`元素给compiler插件的每个目标提供了给定的参数。上面的例子中，compiler插件已经被作为构建过程的一部分被使用，并且就只是改了一下配置。也可能需要添加新的目标到构建过程，并且配置特定的目标。对于这些信息，请看[构建生命周期的介绍](http://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)。

想知道插件有哪些配置可以用，你可以看[插件列表](http://maven.apache.org/plugins/)然后去到你想用的插件和目标。关于如何配置插件参数的通用信息，可以看[插件配置指南](http://maven.apache.org/guides/mini/guide-configuring-plugins.html)。

### 如何添加资源到我的JAR包？
不用修改我们上面的POM，另一个能被满足的通用用例就是把资源文件放进JAR包。对于这个通用任务，Maven再次依赖于[标准目录布局](http://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html)，这意味着使用标准Maven约定，你把资源放到标准目录结构中就能把它们打进JAR包。

看下面这个例子，我们已经添加了目录`${basedir}/src/main/resources`，这里我们可以放任何我们想打进JAR包的资源。Maven所使用的这个简单规则是：任何在`${basedir}/src/main/resources`中的目录和文件都会在JAR包中的根目录以同样的目录结构来展现。

		my-app
		|-- pom.xml
		`-- src
		    |-- main
		    |   |-- java
		    |   |   `-- com
		    |   |       `-- mycompany
		    |   |           `-- app
		    |   |               `-- App.java
		    |   `-- resources
		    |       `-- META-INF
		    |           `-- application.properties
		    `-- test
		        `-- java
		            `-- com
		                `-- mycompany
		                    `-- app
		                        `-- AppTest.java
所以你可以看到例子中我们有一个`META-INF`目录并包含一个`application.properties`文件在这个目录中。如果展开Maven生成好的JAR包，你可以看到如下结构：

		|-- META-INF
		|   |-- MANIFEST.MF
		|   |-- application.properties
		|   `-- maven
		|       `-- com.mycompany.app
		|           `-- my-app
		|               |-- pom.properties
		|               `-- pom.xml
		`-- com
		    `-- mycompany
		        `-- app
		            `-- App.class

像你看到的，`${basedir}/src/main/resources`里的内容可以在JAR包的根目录找到，`META-INF`中的`application.properties`文件也在那里。你同样也会注意到其它如`META-INF/MANIFEST.MF`, `pom.xml`, `pom.properties`文件。这些在Maven中是JAR生成的标准文件。你也可以创建自己的manifest文件，但如果你没创建，Maven会默认帮你创建一个。（你也可以改变默认manifest中的条件，我们之后会讲到） `pom.xml`和`pom.properties`文件被打进JAR包，所以每个Maven生成的工件都是自描述的，并且如果有需求，你也可以利用项目中的元数据。一个简单的用法可能是查询程序的版本号。操作POM文件需要使用一些Maven工具，但properties文件可以直接利用标准Java API进行读取：

		#Generated by Maven
		#Tue Oct 04 15:43:21 GMT-05:00 2005
		version=1.0-SNAPSHOT
		groupId=com.mycompany.app
		artifactId=my-app

想添加资源到单元测试的classpath，你可以遵循相同的模式，除了要把资源放到`${basedir}/src/test/resources`中。这时你应该有一个像这样的目录结构：

		my-app
		|-- pom.xml
		`-- src
		    |-- main
		    |   |-- java
		    |   |   `-- com
		    |   |       `-- mycompany
		    |   |           `-- app
		    |   |               `-- App.java
		    |   `-- resources
		    |       `-- META-INF
		    |           |-- application.properties
		    `-- test
		        |-- java
		        |   `-- com
		        |       `-- mycompany
		        |           `-- app
		        |               `-- AppTest.java
		        `-- resources
		            `-- test.properties

单元测试中你可以用一个像这样的简单代码片段来访问测试需要的资源：

		...
		 
		// Retrieve resource
		InputStream is = getClass().getResourceAsStream( "/test.properties" );
		 
		// Do something with the resource
		 
		...
### 如何过滤资源文件？
有时一个资源文件需要包含只能在构建时期提供的值。为了达到这个目的，可以写一个属性的引用，然后把值用表达式`${<property name>}`包含在资源文件中。属性的值可以是一个在pom.xml中定义的值，一个在用户的settings.xml中定义的值，一个在外部properties文件中定义的属性，或者一个系统属性。

在复制时想要一个资源过滤器，只需要在pom.xml中对资源目录设置`filtering`为true：

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
		      <version>4.11</version>
		      <scope>test</scope>
		    </dependency>
		  </dependencies>
		 
		  <build>
		    <resources>
		      <resource>
		        <directory>src/main/resources</directory>
		        <filtering>true</filtering>
		      </resource>
		    </resources>
		  </build>
		</project>

注意到你需要添加之前没有的`build`, `resources`, 和`resource`元素。另外我们也需要明确指出资源位于src/main/resources目录。所有这些信息之前都是作为默认值被提供的，但因为`filtering`的默认值是false，我们需要覆盖`filtering`的默认值为true。

指定pom.xml中的某个属性，属性名要使用XML元素中定义的值，并用“pom”作为项目根元素的别名。所以，`${pom.name}`指的是项目名称，`${pom.version}`指的是项目版本，`${pom.build.finalName}`指的是当这个项目被打包时生成的文件的名字，等等。注意到POM中一些的元素有默认值，所以我们不用明确的在`pom.xml`中定义它们就可以在这使用。类似的，用户`settings.xml`中定义的属性名以“setting”开头（例如，`${settings.localRepository}`指的是用户本地仓库的路径）。

为了继续我们的例子，让我们添加一些属性到`application.properties`文件（`src/main/resources`目录中），这些属性会在资源被过滤时被提供：

		# application.properties
		application.name=${pom.name}
		application.version=${pom.version}

在这里，可以运行下面的命令（process-resources是资源被复制和过滤的构建生命周期阶段）：

		mvn process-resources

在`target/classes`中的`application.properties`（最终会放到jar里面）文件看起来像这样：

		# application.properties
		application.name=Maven Quick Start Archetype
		application.version=1.0-SNAPSHOT

在外部文件中定义一个属性，你只需要在pom.xml中添加一个外部文件的引用。首先，让我们创建这个`src/main/filters/filter.properties`的外部文件：

		# filter.properties
		my.filter.value=hello!

然后我们把这个新文件的引用添加到pom.xml：

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
		      <version>4.11</version>
		      <scope>test</scope>
		    </dependency>
		  </dependencies>
		 
		  <build>
		    <filters>
		      <filter>src/main/filters/filter.properties</filter>
		    </filters>
		    <resources>
		      <resource>
		        <directory>src/main/resources</directory>
		        <filtering>true</filtering>
		      </resource>
		    </resources>
		  </build>
		</project>

然后如果你想引用`application.properties`中的属性：

		# application.properties
		application.name=${pom.name}
		application.version=${pom.version}
		message=${my.filter.value}

再次执行`mvn process-resources`会把新的属性值放到`application.properties`中。作为一个在外部文件中定义my.filter.value属性的替代方案，你也可以在`pom.xml`中的`properties`部分定义它，效果是一样的（这时可以不用`src/main/filters/filter.properties`的引用）。

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
		      <version>4.11</version>
		      <scope>test</scope>
		    </dependency>
		  </dependencies>
		 
		  <build>
		    <resources>
		      <resource>
		        <directory>src/main/resources</directory>
		        <filtering>true</filtering>
		      </resource>
		    </resources>
		  </build>
		 
		  <properties>
		    <my.filter.value>hello</my.filter.value>
		  </properties>
		</project>

过滤资源也可以从系统属性中取值；系统属性也可以被构建到Java中（例如`java.version`或`user.home`）或在命令行使用标准Java -D参数定义的属性。为了完成这个例子，我们把`application.properties`文件改成这样：

		# application.properties
		java.version=${java.version}
		command.line.prop=${command.line.prop}
	
现在当我们执行下面这条命令时（注意命令行中command.line.prop的定义），`application.properties`文件会包含系统属性的值。

		mvn process-resources "-Dcommand.line.prop=hello again"

### 如何使用外部依赖？
你可能已经注意到我们用的POM中的`dependencies`元素。事实上你已经在使用外部依赖，但是这会我们来详细说下这是如何工作的。更透彻的介绍，请参考[依赖机制介绍](http://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html)

pom.xml的`dependencies`部分列出了需要用来构建项目的所有外部依赖（不管是否它是在编译时，测试时，运行时还是其它什么时候需要）。现在我们的项目只依赖于Junit（为了清晰，去掉了资源过滤）：

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
		      <version>4.11</version>
		      <scope>test</scope>
		    </dependency>
		  </dependencies>
		</project>

对于每个外部依赖，你至少需要定义4个部分：groupId, artifactId, version, 和scope。 groupId, artifactId 和 version与构建这个依赖的项目中POM一样。scope元素指定了你的项目如何使用依赖，它可以写入`compile`, `test`, 和 `runtime` 的值。 更多关于依赖的设置信息，请参考[项目描述器参考](http://maven.apache.org/ref/current/maven-model/maven.html)。

更多关于依赖机制，请看[依赖机制介绍](http://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html)。

有了关于依赖的这些信息，Maven就可以在构建项目时引用这个依赖。 Maven从哪里引用这些依赖呢？它会在本地仓库(默认位置在`~/.m2/repository`)找所有的依赖。在之前的部分，我们从我们的项目安装了一个工件（my-app-1.0-SNAPSHOT.jar）到本地仓库。一旦项目被安装，其它项目就可以通过在它们自己的pom.xml中添加依赖的方式来引用它：

		<project xmlns="http://maven.apache.org/POM/4.0.0"
		  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
		                      http://maven.apache.org/xsd/maven-4.0.0.xsd">
		  <groupId>com.mycompany.app</groupId>
		  <artifactId>my-other-app</artifactId>
		  ...
		  <dependencies>
		    ...
		    <dependency>
		      <groupId>com.mycompany.app</groupId>
		      <artifactId>my-app</artifactId>
		      <version>1.0-SNAPSHOT</version>
		      <scope>compile</scope>
		    </dependency>
		  </dependencies>
		</project>

其它地方构建的依赖呢？如何把它们弄到我的本地仓库中？无论何时项目引用一个本地仓库中不存在的依赖，Maven会把这个依赖从远程仓库中下载到本地仓库。你可能注意到当构建你第一个项目时Maven下载了很多东西（这些下载都是很多构建项目的插件需要的依赖）。 默认的Maven远程仓库是[http://repo.maven.apache.org/maven2/](http://repo.maven.apache.org/maven2/)。你也可以设置你自己的远程仓库（可能是你公司的中央库）来取代默认远程仓库或作为默认仓库的补充。关于仓库的更多信息，请参考[仓库介绍](http://maven.apache.org/guides/introduction/introduction-to-repositories.html)。

来为我们的工程添加一个依赖。假如说我们想加入代码日志，需要把log4j作为一个依赖。首先，我们需要知道log4j的groupId, artifactId,和 version 。 我们可以浏览ibiblio来查找它，或者用Google来搜索“site:www.ibiblio.org maven2 log4j”。搜索结果显示一个叫/maven2/log4j/log4j的目录（或 /pub/packages/maven2/log4j/log4j）。 在目录里我们找到一个叫maven-metadata.xml的文件。maven-metadata.xml里的内容看来像这样：

		<metadata>
		  <groupId>log4j</groupId>
		  <artifactId>log4j</artifactId>
		  <version>1.1.3</version>
		  <versioning>
		    <versions>
		      <version>1.1.3</version>
		      <version>1.2.4</version>
		      <version>1.2.5</version>
		      <version>1.2.6</version>
		      <version>1.2.7</version>
		      <version>1.2.8</version>
		      <version>1.2.11</version>
		      <version>1.2.9</version>
		      <version>1.2.12</version>
		    </versions>
		  </versioning>
		</metadata>

从这个文件，我们可以看到gourpId是“log4j”，artifactId是“log4j”。我们也看到很多不同的版本号可选；现在我们用最新的版本，1.2.12 （有些文件里也会指出哪个版本是当前的发布版本）。maven-metadata.xml文件的旁边，我们可以看到一个目录对应不同版本的log4j。在它们每一个里面，我们可以找到真实的jar文件（如log4j-1.2.12.jar）以及pom文件（这个是为了指出还有哪些更深的依赖和其它信息）和另一个maven-metadata.xml文件。同时每个版本也有一个对应的MD5文件，包含了每个文件的MD5散列值。你可以使用这个来验证包文件或者找出你已经在用的包是哪个版本。

现在我们已经有了需要的信息，我们可以添加依赖到我们的pom.xml:

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
		      <version>4.11</version>
		      <scope>test</scope>
		    </dependency>
		    <dependency>
		      <groupId>log4j</groupId>
		      <artifactId>log4j</artifactId>
		      <version>1.2.12</version>
		      <scope>compile</scope>
		    </dependency>
		  </dependencies>
		</project>

现在，当我们编译项目时（`mvn compile`）,我们可以看到Maven为我们下载了log4j依赖。

### 如何部署JAR包到远程仓库？
为了把我们的包部署到外部仓库上，我们需要在pom.xml中配置仓库的URL，并且在settings.xml中配置连接到仓库的验证信息。

这是使用scp和用户名密码验证的一个例子：

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
		      <version>4.11</version>
		      <scope>test</scope>
		    </dependency>
		    <dependency>
		      <groupId>org.apache.codehaus.plexus</groupId>
		      <artifactId>plexus-utils</artifactId>
		      <version>1.0.4</version>
		    </dependency>
		  </dependencies>
		 
		  <build>
		    <filters>
		      <filter>src/main/filters/filters.properties</filter>
		    </filters>
		    <resources>
		      <resource>
		        <directory>src/main/resources</directory>
		        <filtering>true</filtering>
		      </resource>
		    </resources>
		  </build>
		  <!--
		   |
		   |
		   |
		   -->
		  <distributionManagement>
		    <repository>
		      <id>mycompany-repository</id>
		      <name>MyCompany Repository</name>
		      <url>scp://repository.mycompany.com/repository/maven2</url>
		    </repository>
		  </distributionManagement>
		</project>

.

		<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
		  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
		                      http://maven.apache.org/xsd/settings-1.0.0.xsd">
		  ...
		  <servers>
		    <server>
		      <id>mycompany-repository</id>
		      <username>jvanzyl</username>
		      <!-- Default value is ~/.ssh/id_dsa -->
		      <privateKey>/path/to/identity</privateKey> (default is ~/.ssh/id_dsa)
		      <passphrase>my_key_passphrase</passphrase>
		    </server>
		  </servers>
		  ...
		</settings>

注意如果你连接到一个openssh ssh服务器，而PasswordAuthentication在sshd_config中设置为了“no”，你将必须每次都要输入你的用户名密码（虽然你可以输入用户名和密码使用另一个SSH客户端登陆）。在这个例子中你可能想切换到公开密钥验证。

请妥善保管settings.xml中使用的密码。更多信息，请看[密码加密](http://maven.apache.org/guides/mini/guide-encryption.html)。

### 如何创建文档？
开始使用Maven的文档系统，你可以运行以下命令，使用原型机制为你已有的项目生成一个站点：

		mvn archetype:generate \
		  -DarchetypeGroupId=org.apache.maven.archetypes \
		  -DarchetypeArtifactId=maven-archetype-site \
		  -DgroupId=com.mycompany.app \
		  -DartifactId=my-app-site

现在去看看[创建站点指南](http://maven.apache.org/guides/mini/guide-site.html)，学习如何为你的项目创建文档吧。
### 如何构建其它类型的项目？
注意，生命周期适用于其它项目类型。例如回到基础目录，我们再创建一个简单的Web应用：

		mvn archetype:generate \
		    -DarchetypeGroupId=org.apache.maven.archetypes \
		    -DarchetypeArtifactId=maven-archetype-webapp \
		    -DgroupId=com.mycompany.app \
		    -DartifactId=my-webapp

注意这些必须写在一行以内。这样会创建一个叫`my-webapp`的目录，里面包含以下项目描述器：

		<project xmlns="http://maven.apache.org/POM/4.0.0"
		  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
		                      http://maven.apache.org/xsd/maven-4.0.0.xsd">
		  <modelVersion>4.0.0</modelVersion>
		 
		  <groupId>com.mycompany.app</groupId>
		  <artifactId>my-webapp</artifactId>
		  <version>1.0-SNAPSHOT</version>
		  <packaging>war</packaging>
		 
		  <dependencies>
		    <dependency>
		      <groupId>junit</groupId>
		      <artifactId>junit</artifactId>
		      <version>4.11</version>
		      <scope>test</scope>
		    </dependency>
		  </dependencies>
		 
		  <build>
		    <finalName>my-webapp</finalName>
		  </build>
		</project>

注意`<packaging>`元素－它告诉Maven需要构建一个WAR。 去到web应用的项目目录运行：

		mvn clean package

你会发现`target/my-webapp.war`被构建，并且所有的常规步骤都被执行了。

### 如果一次构建多个项目？
处理多模块的概念也被内建到Maven中了。在这个部分，我们看看如何一步就构建一个WAR，同时包含上面的一个JAR。

首先，我们需要添加一个父pom.xml文件在其它两个之上，看起来像这样：

		+- pom.xml
		+- my-app
		| +- pom.xml
		| +- src
		|   +- main
		|     +- java
		+- my-webapp
		| +- pom.xml
		| +- src
		|   +- main
		|     +- webapp

新创建的POM文件应该包含：

		<project xmlns="http://maven.apache.org/POM/4.0.0"
		  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
		                      http://maven.apache.org/xsd/maven-4.0.0.xsd">
		  <modelVersion>4.0.0</modelVersion>
		 
		  <groupId>com.mycompany.app</groupId>
		  <artifactId>app</artifactId>
		  <version>1.0-SNAPSHOT</version>
		  <packaging>pom</packaging>
		 
		  <modules>
		    <module>my-app</module>
		    <module>my-webapp</module>
		  </modules>
		</project>

我们还需要在webapp中的一个JAR依赖，所以在`my-webapp/pom.xml`中加入：

		  ...
		  <dependencies>
		    <dependency>
		      <groupId>com.mycompany.app</groupId>
		      <artifactId>my-app</artifactId>
		      <version>1.0-SNAPSHOT</version>
		    </dependency>
		    ...
		  </dependencies>

最后，在两个子目录中的pom.xml中加入这个`<parent>`元素：

		<project xmlns="http://maven.apache.org/POM/4.0.0"
		  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
		                      http://maven.apache.org/xsd/maven-4.0.0.xsd">
		  <parent>
		    <groupId>com.mycompany.app</groupId>
		    <artifactId>app</artifactId>
		    <version>1.0-SNAPSHOT</version>
		  </parent>
		  ...

现在从顶层目录里来试试，运行：

		mvn clean install

WAR文件已经被创建在`my-webapp/target/my-webapp.war`，并且JAR也被包含：

		$ jar tvf my-webapp/target/my-webapp-1.0-SNAPSHOT.war
		   0 Fri Jun 24 10:59:56 EST 2005 META-INF/
		 222 Fri Jun 24 10:59:54 EST 2005 META-INF/MANIFEST.MF
		   0 Fri Jun 24 10:59:56 EST 2005 META-INF/maven/
		   0 Fri Jun 24 10:59:56 EST 2005 META-INF/maven/com.mycompany.app/
		   0 Fri Jun 24 10:59:56 EST 2005 META-INF/maven/com.mycompany.app/my-webapp/
		3239 Fri Jun 24 10:59:56 EST 2005 META-INF/maven/com.mycompany.app/my-webapp/pom.xml
		   0 Fri Jun 24 10:59:56 EST 2005 WEB-INF/
		 215 Fri Jun 24 10:59:56 EST 2005 WEB-INF/web.xml
		 123 Fri Jun 24 10:59:56 EST 2005 META-INF/maven/com.mycompany.app/my-webapp/pom.properties
		  52 Fri Jun 24 10:59:56 EST 2005 index.jsp
		   0 Fri Jun 24 10:59:56 EST 2005 WEB-INF/lib/
		2713 Fri Jun 24 10:59:56 EST 2005 WEB-INF/lib/my-app-1.0-SNAPSHOT.jar

这是怎么做到的？首先，父POM创建（叫`app`）,打包类型为`pom`，并且定义了一些模块。这告诉Maven基于这一系列的项目来运行所有操作，而不是仅仅是运行一个（想覆盖这个行为，你可以用`--non-recursive`命令行选项）。

然后，我们告诉WAR它需要`my-app`的JAR包。这完成了很多东西：它使得WAR中的任何代码在classpath中都可用，确认JAR包总会在WAR包之前被构建，而且它要求WAR 插件把JAR包包含到它的包目录中。

你可能注意到junit-4.11.jar是一个依赖，但在WAR中并没有包含。原因是它是一个`<scope>test</scope>`元素－只在测试时需要，所以不会像compile的依赖my-app一样，被包含到web应用里。

最后一步是包含一个父定义。这与你在Maven 1.0中熟悉的扩展元素是不同的：它保证了POM总会通过在仓库中查找父项目被找到，即使这些项目是分开发行。

与Maven 1.0不同，这里不需要运行`install`来完成这些步骤－你可以自己运行`package`，然后其中的工件将会在target目录中被用到，而不是到本地仓库中找。

你可能想要再次生成IDEA工作空间：

		mvn idea:idea