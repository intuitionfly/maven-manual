# 可用的插件
Maven 的核心部分是一个插件执行框架；所有的工作都是由插件完成的。 正在找某个需要执行的特定目标？本页列出了可用的核心插件与其它插件。 有构建和报表的插件：

* **构建插件** 将会在构建阶段执行。它们应该被配置到POM的`<build/>`节点中。
* **报表插件** 将会在生成站点的时候被执行。它们应该被配置到POM的`<reporting/>`节点中。因为报表插件执行的结果是生成站点的一部分，所以报表插件应该同时被国际化和本地化。你可以了解更多关于[插件的本地化](http://maven.apache.org/plugins/localization.html)，以及你可以怎样提供帮助。

## Maven项目支持的插件
浏览Maven仓库的`org/apache/maven/plugins`子目录可以看到最新的插件列表。(*插件是根据标准Java包的命名规范组织而成的目录结构*)

<table border="0">
<tr>
<th align="left"><b>插件</b></th>
<th align="left"><b>类型*</b></th>
<th align="left"><b>版本</b></th>
<th align="left"><b>发布日期</b></th>
<th align="left"><b>描述</b></th>
<th align="left"><b>代码仓库</b></th>
<th align="left"><b>问题跟踪</b></th></tr>
<tr class="b">
<td align="left"><b>核心插件</b></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><b>对应默认核心阶段的插件(如，clean, compile)。 它们也可能有多个目标。</b></td>
<td align="left"></td>
<td align="left"></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-clean-plugin/index.md"> <tt>clean</tt></a></td>
<td align="left">B</td>
<td align="left">3.0.0</td>
<td align="left">2015-10-22</td>
<td align="left">清除生成的构建内容</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-clean-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MCLEAN">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-compiler-plugin/index.md"> <tt>compiler</tt></a></td>
<td align="left">B</td>
<td align="left">3.5</td>
<td align="left">2016-01-20</td>
<td align="left">编译Java源码</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-compiler-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MCOMPILER">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-deploy-plugin/index.md"> <tt>deploy</tt></a></td>
<td align="left">B</td>
<td align="left">2.8.2</td>
<td align="left">2014-08-27</td>
<td align="left">把构建好的工件部署到远程仓库中</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-deploy-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MDEPLOY">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-failsafe-plugin/index.md"> <tt>failsafe</tt></a></td>
<td align="left">B</td>
<td align="left">2.19.1</td>
<td align="left">2016-01-03</td>
<td align="left">在隔离的类加载器中运行JUnit集成测试</td>
<td align="left"><a class="externalLink" href="https://git-wip-us.apache.org/repos/asf/maven-surefire.git">GIT</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/SUREFIRE">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-install-plugin/index.md"> <tt>install</tt></a></td>
<td align="left">B</td>
<td align="left">2.5.2</td>
<td align="left">2014-08-27</td>
<td align="left">把构建好的工件安装到本地仓库</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-install-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MINSTALL">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-resources-plugin/index.md"> <tt>resources</tt></a></td>
<td align="left">B</td>
<td align="left">2.7</td>
<td align="left">2014-09-29</td>
<td align="left">把资源文件复制到输出目录中，以便包含到JAR包中</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-resources-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MRESOURCES">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-site-plugin/index.md"> <tt>site</tt></a></td>
<td align="left">B</td>
<td align="left">3.4</td>
<td align="left">2014-07-07</td>
<td align="left">为当前的项目生成一个站点</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-site-plugin/">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MSITE">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-surefire-plugin/index.md"> <tt>surefire</tt></a></td>
<td align="left">B</td>
<td align="left">2.19.1</td>
<td align="left">2016-01-03</td>
<td align="left">在隔离的类加载器中运行JUnit单元测试</td>
<td align="left"><a class="externalLink" href="https://git-wip-us.apache.org/repos/asf/maven-surefire.git">GIT</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/SUREFIRE">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-verifier-plugin/index.md"> <tt>verifier</tt></a></td>
<td align="left">B</td>
<td align="left">1.1</td>
<td align="left">2015-04-14</td>
<td align="left">验证特定条件的存在性－在集成测试中很有用</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-verifier-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MVERIFIER">JIRA</a></td></tr>
<tr class="b">
<td align="left"><b>打包类型/工具</b></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><b>这些插件与各自工件类型的打包有关</b></td>
<td align="left"></td>
<td align="left"></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-ear-plugin/index.md"> <tt>ear</tt></a></td>
<td align="left">B</td>
<td align="left">2.10.1</td>
<td align="left">2015-06-27</td>
<td align="left">生成当前项目的EAR包</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-ear-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MEAR">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-ejb-plugin/index.md"> <tt>ejb</tt></a></td>
<td align="left">B</td>
<td align="left">2.5.1</td>
<td align="left">2015-06-20</td>
<td align="left">生成当前项目的EJB包（也可以同时生成client包）</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-ejb-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MEJB">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-jar-plugin/index.md"> <tt>jar</tt></a></td>
<td align="left">B</td>
<td align="left">2.6</td>
<td align="left">2015-03-09</td>
<td align="left">生成当前项目的JAR包</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-jar-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MJAR">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-rar-plugin/index.md"> <tt>rar</tt></a></td>
<td align="left">B</td>
<td align="left">2.4</td>
<td align="left">2014-09-08</td>
<td align="left">生成当前项目的RAR包</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-rar-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MRAR">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-war-plugin/index.md"> <tt>war</tt></a></td>
<td align="left">B</td>
<td align="left">2.6</td>
<td align="left">2015-01-08</td>
<td align="left">生成当前项目的WAR包</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-war-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MWAR">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-acr-plugin/index.md"> <tt>app-client/acr</tt></a></td>
<td align="left">B</td>
<td align="left">1.1</td>
<td align="left">2014-09-02</td>
<td align="left">生成当前项目JavaEE应用的Client包</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-acr-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MACR">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-shade-plugin/index.md"> <tt>shade</tt></a></td>
<td align="left">B</td>
<td align="left">2.4.3</td>
<td align="left">2016-01-10</td>
<td align="left">从当前项目构建一个Uber-JAR并包含所需的依赖</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-shade-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MSHADE">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-source-plugin/index.md"> <tt>source</tt></a></td>
<td align="left">B</td>
<td align="left">2.4</td>
<td align="left">2014-10-07</td>
<td align="left">从当前项目构建一个源码JAR包</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-source-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MSOURCES">JIRA</a></td></tr>
<tr class="a">
<td align="left"><b>报表插件</b></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><b>用于生成报表的插件，在POM中被配置为报表，并在生成站点的生命周期运行。</b></td>
<td align="left"></td>
<td align="left"></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-changelog-plugin/index.md"> <tt>changelog</tt></a></td>
<td align="left">R</td>
<td align="left">2.3</td>
<td align="left">2014-06-24</td>
<td align="left">从SCM中生成近期改动的列表</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-changelog-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MCHANGELOG">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-changes-plugin/index.md"> <tt>changes</tt></a></td>
<td align="left">B+R</td>
<td align="left">2.11</td>
<td align="left">2014-09-28</td>
<td align="left">从问题追踪或变动文档生成报表</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-changes-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MCHANGES">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-checkstyle-plugin/index.md"> <tt>checkstyle</tt></a></td>
<td align="left">B+R</td>
<td align="left">2.17</td>
<td align="left">2015-10-15</td>
<td align="left">生成Checkstyle报表</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-checkstyle-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MCHECKSTYLE">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-doap-plugin/index.md"> <tt>doap</tt></a></td>
<td align="left">B</td>
<td align="left">1.2</td>
<td align="left">2015-03-17</td>
<td align="left">根据POM生成一个项目描述文件</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-doap-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MDOAP">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-docck-plugin/index.md"> <tt>docck</tt></a></td>
<td align="left">B</td>
<td align="left">1.1</td>
<td align="left">2015-04-03</td>
<td align="left">文档检查者插件</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-docck-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MDOCCK">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-javadoc-plugin/index.md"> <tt>javadoc</tt></a></td>
<td align="left">B+R</td>
<td align="left">2.10.3</td>
<td align="left">2015-04-14</td>
<td align="left">为项目生成Javadoc</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-javadoc-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MJAVADOC">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-jdeps-plugin/index.md"> <tt>jdeps</tt></a></td>
<td align="left">B</td>
<td align="left">3.0.0</td>
<td align="left">2015-10-29</td>
<td align="left">在项目上运行JDK的JDeps工具</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-jdeps-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MJDEPS">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-jxr-plugin/index.md"> <tt>jxr</tt></a></td>
<td align="left">R</td>
<td align="left">2.5</td>
<td align="left">2014-11-02</td>
<td align="left">生成源码交叉参考</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/jxr/trunk/maven-jxr-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/JXR">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-linkcheck-plugin/index.md"> <tt>linkcheck</tt></a></td>
<td align="left">R</td>
<td align="left">1.2</td>
<td align="left">2014-10-08</td>
<td align="left">生成项目文档的Linkcheck报表（Doxia LinkCheck）</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-linkcheck-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MLINKCHECK">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-pmd-plugin/index.md"> <tt>pmd</tt></a></td>
<td align="left">B+R</td>
<td align="left">3.6</td>
<td align="left">2015-12-17</td>
<td align="left">生成PMD报表</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-pmd-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MPMD">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-project-info-reports-plugin/index.md"> <tt>project-info-reports</tt></a></td>
<td align="left">R</td>
<td align="left">2.8.1</td>
<td align="left">2015-09-11</td>
<td align="left">生成标准项目报表</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-project-info-reports-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MPIR">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-surefire-report-plugin/index.md"> <tt>surefire-report</tt></a></td>
<td align="left">R</td>
<td align="left">2.19.1</td>
<td align="left">2016-01-03</td>
<td align="left">基于单元测试结果生成报表</td>
<td align="left"><a class="externalLink" href="https://git-wip-us.apache.org/repos/asf/maven-surefire.git">GIT</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/SUREFIRE">JIRA</a></td></tr>
<tr class="b">
<td align="left"><b>工具</b></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"></td>
<td align="left"><b>Maven默认有这些各类工具可以使用。</b></td>
<td align="left"></td>
<td align="left"></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-ant-plugin/index.md"> <tt>ant</tt></a></td>
<td align="left">B</td>
<td align="left">2.4</td>
<td align="left">2014-12-15</td>
<td align="left">为项目生成Ant构建文件</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-ant-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MANT">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-antrun-plugin/index.md"> <tt>antrun</tt></a></td>
<td align="left">B</td>
<td align="left">1.8</td>
<td align="left">2014-12-26</td>
<td align="left">在构建的某个阶段运行一系列ant任务</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-antrun-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MANTRUN">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-archetype-plugin/index.md"> <tt>archetype</tt></a></td>
<td align="left">B</td>
<td align="left">2.4</td>
<td align="left">2015-08-09</td>
<td align="left">从一个原型生成项目的框架结构</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/archetype/trunk/archetype-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/ARCHETYPE">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-assembly-plugin/index.md"> <tt>assembly</tt></a></td>
<td align="left">B</td>
<td align="left">2.6</td>
<td align="left">2015-10-10</td>
<td align="left">构建一个源码和（或）二进制文件的程序集（发行版）</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-assembly-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MASSEMBLY">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-dependency-plugin/index.md"> <tt>dependency</tt></a></td>
<td align="left">B+R</td>
<td align="left">2.10</td>
<td align="left">2015-01-27</td>
<td align="left">依赖管理（复制，解压）和分析</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-dependency-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MDEP">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-enforcer-plugin/index.md"> <tt>enforcer</tt></a></td>
<td align="left">B</td>
<td align="left">1.4.1</td>
<td align="left">2015-08-23</td>
<td align="left">环境约束检查(Maven版本, JDK等), 用户定制规则执行</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/enforcer/trunk/maven-enforcer-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MENFORCER">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-gpg-plugin/index.md"> <tt>gpg</tt></a></td>
<td align="left">B</td>
<td align="left">1.6</td>
<td align="left">2015-01-19</td>
<td align="left">为工作和POM创建签名</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-gpg-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MGPG">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-help-plugin/index.md"> <tt>help</tt></a></td>
<td align="left">B</td>
<td align="left">2.2</td>
<td align="left">2013-02-23</td>
<td align="left">获得项目工作环境的信息</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-help-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MPH">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-invoker-plugin/index.md"> <tt>invoker</tt></a></td>
<td align="left">B+R</td>
<td align="left">2.0.0</td>
<td align="left">2015-06-27</td>
<td align="left">运行一系列的Maven工程并验证输出</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-invoker-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="http://jira.codehaus.org/browse/MINVOKER">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-jarsigner-plugin/index.md"> <tt>jarsigner</tt></a></td>
<td align="left">B</td>
<td align="left">1.4</td>
<td align="left">2015-01-21</td>
<td align="left">签名或验证项目工件</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-jarsigner-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MJARSIGNER">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-patch-plugin/index.md"> <tt>patch</tt></a></td>
<td align="left">B</td>
<td align="left">1.2</td>
<td align="left">2015-03-09</td>
<td align="left">使用GNU补丁工具把补丁文件应用到源码中</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-patch-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MPATCH">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-pdf-plugin/index.md"> <tt>pdf</tt></a></td>
<td align="left">B</td>
<td align="left">1.3</td>
<td align="left">2015-02-16</td>
<td align="left">生成项目文档的PDF版本</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-pdf-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MPDF">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-plugin-plugin/index.md"> <tt>plugin</tt></a></td>
<td align="left">B+R</td>
<td align="left">3.4</td>
<td align="left">2015-01-04</td>
<td align="left">为源码树中找到的MOJO生成Maven插件的描述器，以便包含到JAR包中</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugin-tools/trunk/maven-plugin-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MPLUGIN">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-release-plugin/index.md"> <tt>release</tt></a></td>
<td align="left">B</td>
<td align="left">2.5.3</td>
<td align="left">2015-10-17</td>
<td align="left">发布当前的项目 - 更新POM并在代码管理系统中打tag</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/release/trunk/maven-release-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MRELEASE">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-remote-resources-plugin/index.md"> <tt>remote-resources</tt></a></td>
<td align="left">B</td>
<td align="left">1.5</td>
<td align="left">2013-08-14</td>
<td align="left">复制远程资源到输出目录，以便包含到工件中</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-remote-resources-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MRRESOURCES">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-repository-plugin/index.md"> <tt>repository</tt></a></td>
<td align="left">B</td>
<td align="left">2.4</td>
<td align="left">2015-02-22</td>
<td align="left">对基于仓库的任务提供帮助的插件</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-repository-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MREPOSITORY">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-scm-plugin/index.md"> <tt>scm</tt></a></td>
<td align="left">B</td>
<td align="left">1.9.4</td>
<td align="left">2015-04-01</td>
<td align="left">对当前项目执行SCM命令</td>
<td align="left"><a class="externalLink" href="https://git-wip-us.apache.org/repos/asf/maven-scm.git ">GIT</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/SCM">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-scm-publish-plugin/index.md"> <tt>scm-publish</tt></a></td>
<td align="left">B</td>
<td align="left">1.1</td>
<td align="left">2014-05-18</td>
<td align="left">把生成的Maven网站发布到SCM中</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-scm-publish-plugin/">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MSCMPUB">JIRA</a></td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-stage-plugin/index.md"> <tt>stage</tt></a></td>
<td align="left">B</td>
<td align="left">1.0</td>
<td align="left">2015-03-03</td>
<td align="left">帮助发布的演示和提升</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-stage-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MSTAGE">JIRA</a></td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-toolchains-plugin/index.md"> <tt>toolchains</tt></a></td>
<td align="left">B</td>
<td align="left">1.1</td>
<td align="left">2014-11-12</td>
<td align="left">允许跨插件的配置共享</td>
<td align="left"><a class="externalLink" href="http://svn.apache.org/repos/asf/maven/plugins/trunk/maven-toolchains-plugin">SVN</a></td>
<td align="left"><a class="externalLink" href="https://issues.apache.org/jira/browse/MTOOLCHAINS">JIRA</a></td></tr></table>

\* 构建或报表插件

也有一些沙箱插件在我们的[代码仓库](http://svn.apache.org/repos/asf/maven/sandbox/trunk/plugins)中。

以前插件参考文档的归档版本可以看[这里](http://maven.apache.org/plugins-archives/)。

## 退役的插件
<table border="0" class="table table-striped">
<tr class="a">
<th align="left"><b>Plugin</b></th>
<th align="left"><b>Type*</b></th>
<th align="left"><b>Version</b></th>
<th align="left"><b>Retired Date</b></th>
<th align="left"><b>Description</b></th></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-eclipse-plugin/index.md"> <tt>eclipse</tt></a></td>
<td align="left">B</td>
<td align="left">2.10</td>
<td align="left">2015-10-07</td>
<td align="left">为当前项目生成一个Eclipse项目</td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-idea-plugin/index.md"> <tt>idea</tt></a></td>
<td align="left">B</td>
<td align="left">2.2.1</td>
<td align="left">2013-07-26</td>
<td align="left">为当前项目创建/更新一个IDEA工作空间(独立模块作为IDEA模块被创建)</td></tr>
<tr class="b">
<td align="left"><a href="/plugins/maven-one-plugin/index.md"> <tt>one</tt></a></td>
<td align="left">B</td>
<td align="left">1.3</td>
<td align="left">2013-07-30</td>
<td align="left">与传统的Maven 1.x仓库和构建进行交互的插件</td></tr>
<tr class="a">
<td align="left"><a href="/plugins/maven-reactor-plugin/index.md"> <tt>reactor</tt></a></td>
<td align="left">B</td>
<td align="left">1.1</td>
<td align="left">2014-03-24</td>
<td align="left">构建在反应器中相互依赖的项目的子集(仅用在Maven 2).</td></tr></table>

## Maven版图以外的插件
### codehaus.org

> 因为codehaus.org的关闭，所有的插件正在[迁移](http://www.mojohaus.org/)到新的地方。 这意味着现在一些链接可能是无效的。 我们也正在不断的清理这些链接。

也有些[插件](http://www.mojohaus.org/plugins.html)在GitHub的 [MojoHaus](https://github.com/mojohaus) 项目中。

这里是一些通用的插件：

<table border="0" class="table table-striped">
<tr class="a">
<th align="left"><b>插件</b> (参看 <a class="externalLink" href="http://www.mojohaus.org/plugins.html">完整列表</a>)</th>
<th align="left"><b>描述</b></th></tr>
<tr class="b">
<td align="left"><a class="externalLink" href="http://mojo.codehaus.org/animal-sniffer-maven-plugin/"> <tt>animal-sniffer</tt></a></td>
<td align="left">构建API（例如JDK）的签名并检查你针对这些接口的类</td></tr>
<tr class="a">
<td align="left"><a class="externalLink" href="http://www.mojohaus.org/build-helper-maven-plugin/"> <tt>build-helper</tt></a></td>
<td align="left">附加更多需要构建的工件和源目录</td></tr>
<tr class="b">
<td align="left"><a class="externalLink" href="http://www.mojohaus.org/castor-maven-plugin/"> <tt>castor</tt></a></td>
<td align="left">使用Castor从XSD生成源码</td></tr>
<tr class="a">
<td align="left"><a class="externalLink" href="http://www.mojohaus.org/clirr-maven-plugin/"> <tt>clirr</tt></a></td>
<td align="left">用Clirr比较二进制文件或源码的兼容性</td></tr>
<tr class="b">
<td align="left"><a class="externalLink" href="http://mojo.codehaus.org/javacc-maven-plugin/"> <tt>javacc</tt></a></td>
<td align="left">根据JavaCC语法生成源码</td></tr>
<tr class="a">
<td align="left"><a class="externalLink" href="http://www.mojohaus.org/jdepend-maven-plugin/"> <tt>jdepend</tt></a></td>
<td align="left">使用JDepend生成代码度量的报告</td></tr>
<tr class="b">
<td align="left"><a class="externalLink" href="http://maven-nar.github.io/"> <tt>nar-maven-plugin</tt></a></td>
<td align="left">为不同的架构编译C, C++, Fortran</td></tr>
<tr class="a">
<td align="left"><a class="externalLink" href="http://www.mojohaus.org/maven-native/native-maven-plugin/"> <tt>native</tt></a></td>
<td align="left">用原生编译器编译C 和 C++ 代码</td></tr>
<tr class="b">
<td align="left"><a class="externalLink" href="http://www.mojohaus.org/sql-maven-plugin/"> <tt>sql</tt></a></td>
<td align="left">运行文件中或直接输入的SQL脚本</td></tr>
<tr class="a">
<td align="left"><a class="externalLink" href="http://www.mojohaus.org/taglist-maven-plugin/"> <tt>taglist</tt></a></td>
<td align="left">基于代码中的tag生成一系列任务</td></tr>
<tr class="b">
<td align="left"><a class="externalLink" href="http://www.mojohaus.org/versions-maven-plugin/"> <tt>versions</tt></a></td>
<td align="left">管理项目及其模块，依赖与插件的版本</td></tr></table>

### code.google.com

也有一些 [插件](http://code.google.com/hosting/search?q=maven+plugin+label%3Amaven&projectsearch=Search+Projects)在 [Google Code](http://code.google.com/)上。

### 其它

很多其它项目提供了它们自己的Maven插件，包括：

<table border="0" class="table table-striped">
<tr class="a">
<th align="left"><b>插件</b></th>
<th align="left"><b>维护者</b></th>
<th align="left"><b>描述</b></th></tr>
<tr class="b">
<td align="left"><a class="externalLink" href="https://codehaus-cargo.github.io/"> <tt>cargo</tt></a></td>
<td align="left"><a class="externalLink" href="https://codehaus-cargo.github.io/">Cargo Project</a></td>
<td align="left">启动/停止/配置 J2EE容器并进行部署</td></tr>
<tr class="a">
<td align="left"><a class="externalLink" href="http://confluence.atlassian.com/display/CLOVER/Clover-for-Maven+2"> <tt>clover</tt></a></td>
<td align="left"><a class="externalLink" href="http://www.atlassian.com/software/clover/">Atlassian Clover</a></td>
<td align="left">生成Clover报表</td></tr>
<tr class="b">
<td align="left"><a class="externalLink" href="http://www.eclipse.org/jetty/documentation/current/jetty-maven-plugin.html"> <tt>jetty</tt></a></td>
<td align="left"><a class="externalLink" href="http://www.eclipse.org/jetty/">Jetty Project</a></td>
<td align="left">运行一个Jetty容器进行快速的Web应用部署</td></tr>
<tr class="a">
<td align="left"><a class="externalLink" href="http://www.triemax.com/products/jalopy/manual/plugin-maven.html"> <tt>jalopy</tt></a></td>
<td align="left"><a class="externalLink" href="http://www.triemax.com/">Triemax</a></td>
<td align="left">使用Jalopy对代码进行格式化</td></tr>
<tr class="b">
<td align="left"><a class="externalLink" href="http://creadur.apache.org/rat/"> <tt>rat</tt></a></td>
<td align="left"><a class="externalLink" href="http://creadur.apache.org/">Apache Creadur Project</a></td>
<td align="left">用Release Audit Tool (RAT)来检查文件</td></tr>
<tr class="a">
<td align="left"><a class="externalLink" href="http://geronimo.apache.org/maven/genesis/plugins/tools-maven-plugin/index.html"> <tt>Genesis Plugins</tt></a></td>
<td align="left"><a class="externalLink" href="http://geronimo.apache.org/">Apache Geronimo Project</a></td>
<td align="left">验证工件中的传统文件</td></tr>
<tr class="b">
<td align="left"><a class="externalLink" href="http://tomcat.apache.org/maven-plugin.html"> <tt>Apache Tomcat</tt></a></td>
<td align="left"><a class="externalLink" href="http://tomcat.apache.org/maven-plugin.html">Apache Tomcat Project</a></td>
<td align="left">运行Apache Tomcat容器来快速部署Web应用</td></tr></table>

## 资源
1. [插件配置指南](http://maven.apache.org/guides/mini/guide-configuring-plugins.html)