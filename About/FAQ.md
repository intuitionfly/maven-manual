# Frequently Asked Technical Questions
1. How do I prevent "[WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!"

	This or a similar warning is emitted by a plugin that processes plain text files but has not been configured to use a specific file encoding. So eliminating the warning is simply a matter of finding out which plugin emits it and how to configure the file encoding for it. This is as easy as adding the following property to your POM (or one of its parent POMs):

		<project>
			...
			<properties>
				<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
			</properties>
			...
		</project>

1. How do I prevent including JARs in WEB-INF/lib? I need a "compile only" scope!
1. How do I list available plugins?
1. How do I determine what version of a plugin I am using?
1. How can I use Ant tasks in a Maven build?
1. How can I use Maven features in an Ant build?
1. How do I set up Maven so it will compile with a target and source JVM of my choice?
1. Is it possible to create my own directory structure?
1. Where is the source code? I couldn't seem to find a link anywhere on the Maven site.
1. Maven can't seem to download the dependencies. Is my installation correct?
1. I have a jar that I want to put into my local repository. How can I copy it in?
1. How do I unsubscribe from Maven mailing lists?
1. How do I skip the tests?
1. How can I run a single unit test?
1. Handle special characters in site
1. How do I include tools.jar in my dependencies?
1. Maven compiles my test classes but doesn't run them?
1. Where are Maven SNAPSHOT artifacts?
1. Where are the Maven XSD schemas?
1. Maven doesn't work, how do I get help?
1. How to produce execution debug output or error messages?
1. What is a Mojo?
1. How to find dependencies on public Maven repositories?

How do I prevent "[WARNING] Using platform encoding (Cp1252 actually) to copy filtered resources, i.e. build is platform dependent!"



