
Instead of writing long scripts for building your projects and manually downloading the dependencies, why not use Maven and get rid of this mess. This article will cover everything that you need to get started with using Maven for your project. After thoroughly understanding this Maven tutorial, the next probable step will be to learn Jenkins which covers the Continuous Integration phase of DevOps.  
  
In this blog on Maven tutorial, we will cover the following topics:

1. Why do we need Maven?
2. What is Maven?
3. Maven Architecture
4. Maven life cycle, phases and goals
5. Demo project.

# Why do we need Maven?

If you are working on Java projects then most of the time you need dependencies. Dependencies are nothing but libraries or JAR files. You need to download and add them manually. Also, the task of upgrading the software stack for your project was done manually before Maven. So there was a need for a better build tool that would handle such issues.

This where Maven comes into the picture. Maven can solve all your problems related to dependencies. You just need to specify the dependencies and the software version that you want in pom.xml file in Maven and Maven will take care of the rest. So now let us try to understand what exactly Maven is.

# What is Maven?

The Maven project is developed by Apache Software Foundation where it was formerly a part of the Jakarta project. Maven is a powerful build automation tool that is primarily used for Java-based projects. Maven helps you tackle two critical aspects of building software -

- It describes how software is built
- It describes the dependencies.

Maven prefers convention over configuration. Maven dynamically downloads Java libraries and Maven plug-ins from one or more repositories such as the Maven Central Repository and stores them in a local cache. The artifacts of the local projects can also be updated with this local cache. Maven can also help you build and manage projects written in C#, Ruby, Scala, and other languages.

==Project Object Model(POM) file is an XML file that contains information related to the project and configuration information such as dependencies, source directory, plugin, goals, etc. used by Maven to build the project.== When you execute a maven command you give maven a POM file to execute the commands. Maven reads the pom.xml file to accomplish its configuration and operations.

## Maven Objectives

![](https://miro.medium.com/v2/resize:fit:1007/1*YxM4RbkFddaLGWetkuMwWw.png)

## When should someone use Maven?

1. If there are too many dependencies for the project.
2. When the dependency version update frequently.
3. Continuous builds, integration, and testing can be easily handled by using maven.
4. When one needs an easy way to generate documentation from the source code, compiling the source code, packaging compiled code into JAR files or ZIP files.

# Maven Architecture

![](https://miro.medium.com/v2/resize:fit:792/1*PfKw4ym-rdRac18Tio2vVA.png)

# Maven life cycle, phases and goals

## 1. Maven life cycle

![](https://miro.medium.com/v2/resize:fit:647/1*_ExIIAjHGiQVHS1b7XH-Xw.png)

There is a specific life cycle that Maven follows to deploy and distribute the target project.

There are three built-in life cycles:

- **default** — This is the main life cycle of Maven as it is responsible for project deployment.
- **clean** — This life cycle is used to clean the project and remove all files generated by the previous build.
- **site** — The aim of this life cycle is to create the project’s site documentation.

Each life cycle is made up of a sequence of phases. The default build life cycle consists of 23 phases as it is the main build life cycle of Maven

On the other hand, clean life cycle consists of 3 phases, while the site life cycle is made up of 4 phases.

## 2. Maven Phases

![](https://miro.medium.com/v2/resize:fit:344/1*8aCirBXFbtQihAPRWSlshA.png)

A Maven phase is nothing but a stage in the Maven build life cycle. Each phase executes a specific task.

Here are a few important phases in the default build life cycle -

- **validate** — This phase checks if all information necessary for the build is available
- **compile** — This phase compiles the source code
- **test-compile** — This phase compiles the test source code
- **test** — This phase runs unit tests
- **package** — This phase packages compiled source code into the distributable format (jar, war)
- **integration-test** — This phase processes and deploys the package if needed to run integration tests
- **install** — This phase installs the package to a local repository
- **deploy** — This phase copies the package to the remote repository

Maven executes phases in a specific order. This means that if we run a specific phase using the command such as mvn <phase>, this won’t only execute the specified phase but all the preceding phases as well.

For example, if you run the command mvn deploy, that is, the deploy phase which is the last phase in the default build life cycle, then this will execute all phases prior to the deploy phase as well.

## 3. Maven Goals

A sequence of goals constitutes a phase and each goal executes a specific task. When you run a phase, then Maven executes all the goals in an order that are associated with that phase. The syntax used is plugin: goal. Some of the phases and the default goals bound to them are as follows :

- compiler: compile — compile phase
- compiler: test — test-compile phase
- surefire: test — test phase
- install: install — install phase
- jar and war: war — package phase

A Maven plugin is a group of goals. However, these goals aren’t necessarily all bound to the same phase. For example, the Maven Failsafe plugin which is responsible for running integration tests. For unit testing, you need Maven surefire plugin.

# Demo Project

In this section of the article, we will have a look at a demo project. To demonstrate how to build a project using Maven, I have created a Selenium Java project along with TestNG using Eclipse IDE. This is a very simple program where I have written code to test the title of a website.

The program will automatically launch a web browser, navigate to the website mentioned in the code, fetch the title of that web page and compare it with the expected title. If the actual title and the expected title match, then the test case passes else it fails.

So for this project you need Java, Maven and Eclipse downloaded on your system. The versions that I am using on my system are as follows -

1. **Eclipse** — Enterprise Edition version 4.12.0 (2019–06)
2. **Java** — version 1.8.0_211
3. **Maven** — version 3.6.1

- Apart from this, you need to download TestNG plugin for Eclipse and you can download it using following steps –

1. Open Eclipse and go to Help. In Help click on the Eclipse marketplace.
2. Type TestNG in the Find box and click on Go. In the results, you will see “TestNG for Eclipse”. You need to download it.

- After you set up your system with the above-mentioned things you are all set to create a demo project using Maven. So now I am going to tell you all the steps required to do this.

1. In Eclipse, click on File -> New -> Maven Project.
2. Click on Create a simple project(skip archetype selection) and then click on next.

- Now you will see a window with parameters such as Group Id, Artifact Id and so on.

1. Group Id is the unique Id of a group that owns the project.
2. Artifact Id is the name of the final compilation unit.
3. Version is the version of the created artifact. SNAPSHOT indicates work in progress.
4. Packaging could be jar, war or pom depending on your project. For our project, we will select jar. Then give the name of your project.

![](https://miro.medium.com/v2/resize:fit:450/1*SNGMFf70XEuiUqT25OXnLA.png)

- Once you create the project then you will see the project structure of your Maven project. Here you can see the following things –

1. pom.xml
2. src and target
3. src/main/java
4. src/test/java
5. Maven dependencies

- Now create a class file in src/main/test and name it DemoClass. This class contains the Selenium code that we are using for testing. Now we have added Selenium, TestNG dependencies and Maven compiler and Surefire plugin to the pom.xml file. The code for DemoClass and pom.xml is given below:

**Code for DemoClass**

package maven.selenium.testng;  
import org.openqa.selenium.WebDriver;  
import org.openqa.selenium.chrome.ChromeDriver;  
import org.testng.annotations.Test;  
public class DemoClass {  
[@Test](http://twitter.com/Test)  
public void test() throws InterruptedException {  
// declaration and instantiation of objects/variables  
//System.setProperty("webdriver.gecko.driver","/home/edureka/Downloads/geckodriver");  
//WebDriver driver = new FirefoxDriver();  
//comment the above 2 lines and uncomment below 2 lines to use Chrome  
System.setProperty("webdriver.chrome.driver","C:UsersArvind PhulareDesktopchromedriver.exe");  
WebDriver driver = new ChromeDriver();  
String baseUrl = "[http://newtours.demoaut.com/](http://newtours.demoaut.com/)";  
String expectedTitle = "Welcome: Mercury Tours";  
String actualTitle = "";  
// launch Fire fox and direct it to the Base URL  
driver.get(baseUrl);  
// get the actual value of the title  
actualTitle = driver.getTitle();  
Thread.sleep(3000);  
/*  
* compare the actual title of the page with the expected one and print  
* the result as "Passed" or "Failed"  
*/  
if (actualTitle.contentEquals(expectedTitle)){  
System.out.println("Test Passed!");  
}  
else  
{  
System.out.println("Test Failed");  
}  
//close Fire fox  
driver.close();  
}  
}

**Code for pom.xml**

<project xmlns="[http://maven.apache.org/POM/4.0.0](http://maven.apache.org/POM/4.0.0)" xmlns:xsi="[http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)" xsi:schemaLocation="[http://maven.apache.org/POM/4.0.0](http://maven.apache.org/POM/4.0.0) [http://maven.apache.org/xsd/maven-4.0.0.xsd](http://maven.apache.org/xsd/maven-4.0.0.xsd)">  
<modelVersion>4.0.0</modelVersion>  
<groupId>maven.selenium</groupId>  
<artifactId>maven.selenium.testng</artifactId>  
<version>0.0.1-SNAPSHOT</version>  
<name>EdurekaDemo</name>  
<properties>  
<selenium.version>2.53.1</selenium.version>  
<testng.version>6.9.10</testng.version>  
</properties>  
   
<build>  
<plugins>  
<plugin>  
<groupId>org.apache.maven.plugins</groupId>  
<artifactId>maven-compiler-plugin</artifactId>  
<configuration>  
<source>1.8</source>  
<target>1.8</target>  
</configuration>  
</plugin>  
<plugin>  
<groupId>org.apache.maven.plugins</groupId>  
<artifactId>maven-surefire-plugin</artifactId>  
<version>2.18.1</version>  
<configuration>  
<suiteXmlFiles>  
<suiteXmlFile>testng.xml</suiteXmlFile>  
</suiteXmlFiles>  
</configuration>  
</plugin>  
</plugins>  
</build>  
   
<dependencies>  
<dependency>  
<groupId>org.seleniumhq.selenium</groupId>  
<artifactId>selenium-java</artifactId>  
<version>3.141.59</version>  
</dependency>  
<dependency>  
<groupId>org.testng</groupId>  
<artifactId>testng</artifactId>  
<version>6.14.3</version>  
<scope>test</scope>  
</dependency>  
</dependencies>  
   
</project>

- Before running the project we need to convert the class file DemoClass to a TestNG file. For doing that, right-click on DemoClass → TestNG -> Convert to TestNG.
- Now to run the project, right-click on a project -> Run as -> Maven clean. This will clear the project by removing all the previous builds.
- After Maven clean, you need to test the project since we have written the code for testing the web application. So right-click on project -> Run as -> Maven test. This will open the website and match the title of the website. If it matches then our test case will pass.

![](https://miro.medium.com/v2/resize:fit:450/1*T372ZDdXTMLIU0riuHGUKw.png)

- We can also execute the above commands using a command prompt. For that, we need the path of the pom.xml file.

1. You can get the path by right-clicking on pom.xml file -> Properties -> Location.
2. Copy the path, then open a command prompt and paste it there using cd. cd C:/Users/Arvind Phulare/eclipse-workspace/maven.selenium.testng.
3. Once you do this, you can again type Maven commands such as mvn clean and mvn test.