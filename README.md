

<a href="https://selenium.dev"><img src="https://selenium.dev/images/selenium_logo_square_green.png" width="180" alt="Selenium"/></a>

<b>
 <h2>What is Selenium?</h2>
</b>
<p>Due to the diverse focus
of the software, and confusion in terminology, many people mistake Selenium for a specific product for a single service. Selenium is a free (open source) automated testing environment
that is used to test web applications in
different browsers and on different platforms. We can use different programming languages, such as Java, to create Selenium test scripts, 
C#, Python, Ruby, PHP, etc
. Selenium Software is not just a tool, but a software package (a set of tools),
each part of which meets different needs in the organization of testing. Here is a list of tools that are included in Selenium Software</p>
<ol>
  <li>Selenium WebDriver</li>
  <li>Selenium RC</li>
  <li>Selenium Grid</li>
</ol>

<h2>Why do We need to use Selenium?</h2>
<p>Selenium is now the standard for automating the execution of tests in browsers. Selenium is open source, no licensing costs are required, which is a great advantage
compared to other testing tools</p>
Advantages of using Selenium:
<ul>
  <li>Test scripts can be written in any of these programming languages: Java, Python, 
C #, PHP, Ruby, Perl</li>
  <li>Tests can be performed on any of these operating systems: Windows, Mac, or Linux.</li>
  <li>Tests can be performed in any browser: Mozilla 
Firefox, Internet Explorer, Google Chrome, Microsoft 
Edge, Safari or Opera.</li>
  <li>Selenium can be integrated with tools such as TestNG and JUnit to manage test
cases and generate reports</li>
  <li>Selenium can be integrated with Maven, Jenkins and Docker to ensure continuous testing</li>
</ul>


## Pre-requisites

Before you can start performing Java automation testing with Selenium, you would need to:

- Install the latest **Java development environment** i.e. **JDK 1.6** or higher. We recommend using the latest version.

- Download the latest **Selenium Client** and its **WebDriver bindings** from the [official website](https://www.selenium.dev/downloads/). Latest versions of Selenium Client and WebDriver are ideal for running your automation script on LambdaTest Selenium cloud grid.

- Install **Maven** which supports **JUnit** framework out of the box. **Maven** can be downloaded and installed following the steps from [the official website](https://maven.apache.org/).

#### Selenium Standalone

- Manual Installation - https://github.com/lmc-eu/steward/wiki/Selenium-server-&-browser-drivers
- Automated Installation - https://www.npmjs.com/package/selenium-standalone
- URL - http://localhost:4444/wd/hub

##### Installation and Launch
<ol>
 
 <li>Step I : Install IntelliJ IDEA</li>
  <ul><li>https://www.jetbrains.com/idea/download/?ysclid=lu9zuetvnf195589274&section=windows</li></ul>
 <li>Step II : Install selenium-standalone.Latest stable version 3.141.59</li>
 <ul><li>https://tencrypto.github.io/downloads/</li></ul>

</ol>
<hr>
# In Windows, Run CMD as Administrator
<p>A new version of Java is installed, we check it via the Command line</p>

 ```
selenium-standalone start -- java -version
```


#### Selenium Grid
- URL -http://localhost:4444/grid/console

##### Installation and Launch
- Step III

```
selenium-standalone start -- -role hub
selenium-standalone start -- -role node -hub http://localhost:4444/grid/register
selenium-standalone start -- -role node -hub http://localhost:4444/grid/register -port 5556
```
```
selenium-standalone start -- -role node -hub http://localhost:4444/grid/register -browser browserName=Chrome
selenium-andalone start -- -role node -hub http://localhost:4444/grid/register -port 5556 -browser browserName=chrome,maxInstances=2
```

#### Code Snippets

##### Maven Dependencies

###### JUnit

```xml
  <dependencies>
  
    <dependency>
      <groupId>org.seleniumhq.selenium</groupId>
      <artifactId>selenium-java</artifactId>
      <version>3.13.0</version>
      <scope>test</scope>
    </dependency>

  
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.12</version>
      <scope>test</scope>
    </dependency>
  
  </dependencies>
```
###### Test NG

```xml
  <dependencies>

    <dependency>
      <groupId>org.seleniumhq.selenium</groupId>
      <artifactId>selenium-java</artifactId>
      <version>3.13.0</version>
      <scope>test</scope>
    </dependency>


    <dependency>
      <groupId>org.testng</groupId>
      <artifactId>testng</artifactId>
      <version>6.14.3</version>
      <scope>test</scope>
    </dependency>

  </dependencies>

```

###### Other Dependencies

```xml
    

    <dependency>
      <groupId>org.apache.poi</groupId>
      <artifactId>poi</artifactId>
      <version>3.6</version>
      <scope>test</scope>
    </dependency>

    <dependency>
      <groupId>org.apache.poi</groupId>
      <artifactId>poi-ooxml</artifactId>
      <version>3.6</version>
      <scope>test</scope>
    </dependency>

```
###### Test Selenium Dependencies(Example)
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.testing</groupId>
    <artifactId>selenium-java-test</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>4.17.0</version>
        </dependency>

        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-server</artifactId>
            <version>3.141.59</version>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>RELEASE</version>
            <scope>compile</scope>
        </dependency>
    </dependencies>

    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

</project>
```


###### Chrome Driver/Java Code

```
  ChromeDriverManager.getInstance().setup();
  driver = new ChromeDriver();
```

###### Firefox Driver/Java Code

```
  FirefoxDriverManager.getInstance().setup();
  driver = new FirefoxDriver();
```

######  Test Selenium
```
package org.testing;

import org.junit.Test;
import org.openqa.selenium.Platform;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.remote.DesiredCapabilities;
import org.openqa.selenium.remote.RemoteWebDriver;

import java.net.MalformedURLException;
import java.net.URL;

/**
 * Web page testing class.
 *
 * @version 1.0.0
 * @autor StasTkachenko3
 */
public class Test1 {

    /*
       ______     __
      / ____/__  / /__  ____  (_)_  ______ ___
      \__ \/ _ \/ / _ \/ __ \/ / / / / __ `__ \
    ___/ /  __/ /  __/ / / / / /_/ / / / / / /
    /____/\___/_/\___/_/ /_/_/\__,_/_/ /_/ /_/
    ------------------------------------------

    */

    /**
     * The method opens the page and checks its title in the browser.
     *
     * @throws MalformedURLException
     */
    @Test
    public void test1() throws MalformedURLException {

        DesiredCapabilities capability = new DesiredCapabilities();
        capability.setBrowserName("chrome");
        capability.setPlatform(Platform.WIN10);
        // Create a new driver instance.
        WebDriver driver;
        driver = new RemoteWebDriver(new URL("http://192.168.99.1:4444/wd/hub"), capability);
        driver.manage().window().maximize();
        // Opening a page in the browser.
        driver.get("https://www.youtube.com/watch?v=dQw4w9WgXcQ&ab_channel=RickAstley");
        // Check the page title.
        System.out.println("Title of the page is " + driver.getTitle());
        // After the test you need to close the browser.
        driver.quit();

    }
}
```

   - File -> Import -> Existing Maven Project -> Navigate to the folder where you unzipped the zip
   - Select the right project
- Choose the Spring Boot Application file (search for file with @SpringBootApplication)
- Right Click on the file and Run as Java Application
- You are all Set

## Overview

### Introduction

Writing your first automation test is a lot of fun.

Java is one of the most popular programming languages. Java offers both object oriented and functional programming features. Selenium can be used for screen scraping and automating repeated tasks on browser.

We take an hands-on approach using Eclipse as an IDE to illustrate more than 200 Java Coding Exercises, Puzzles and Code Examples. We will also write more than 100 Selenium automation tests with Java for a wide variety of scenarios.

In more than 350 Steps, we explore the most important Java Programming Features and Selenium Automation Testing Scenarios
- Basics of Java Programming - Expressions, Variables and Printing Output
- Using Selenium IDE and Katalon Studio to Record and Replay Automation Testing Scenarios
- Exporting Automation Tests and Setting up new Maven Project for JUnit and TestNG 
- TestNG vs JUnit
- TestNG Advanced Features - XML Suite, Test Reports, Running Tests with Parameters defined in XML and Running Tests in Parallel
- Basics of HTML, CSS and XPath
- Selenium Locators - By Id, By Name, By Link Text, By Partial Link Text, By Class, CSS Selectors and XPath Expressions
- Setting and Reading values from Form Elements - Text, TextArea, CheckBox , Radio Button, Select Box and Multi Select Box
- Advanced Selenium Automation Testing Scenarios - Playing with Windows, Modal Windows (Sleep, Implicit Wait and Explicit Waits), Alert Boxes, Window Handles and New Browser Window Launches, Frames, Taking Screenshots, Executing JavaScript Code, Actions Interface to control mouse and keyboard
- Set up Automation Testing Frameworks - Tables
- Important Interfaces - WebDriver
- Introduction to Cross Browser Automation Testing, Headless Testing and Setting up a Basic Cross Browser Automation Testing Framework
- Writing Data Driven Testing with Data Providers, CSV and Excel Spreadsheets
- Implementing Page Object Model for a Complex Test Scenario
- Scaling up with Selenium Standalone and Grid
- Java Operators - Java Assignment Operator, Relational and Logical Operators, Short Circuit Operators
- Java Conditionals and If Statement
- Methods - Parameters, Arguments and Return Values
- An Overview Of Java Platform - java, javac, bytecode, JVM and Platform Independence - JDK vs JRE vs JVM
- Object Oriented Programming - Class, Object, State and Behavior
- Basics of OOPS - Encapsulation, Abstraction, Inheritance and Polymorphism
- Basics about Java Data Types - Casting, Operators and More
- Java Built in Classes - BigDecimal, String, Java Wrapper Classes
- Conditionals with Java - If Else Statement, Nested If Else, Java Switch Statement, Java Ternary Operator
- Loops - For Loop, While Loop in Java, Do While Loop, Break and Continue
- Java Array and ArrayList - Java String Arrays, Arrays of Objects, Primitive Data Types, toString and Exceptions
- Java Collections - List Interface(ArrayList, LinkedList and Vector), Set Interface (HashSet, LinkedHashSet and TreeSet), Queue Interface (PriorityQueue) and Map Interface (HashMap, HashTable, LinkedHashMap and TreeMap() - Compare, Contrast and Choose
- Generics - Why do we need Generics? Restrictions with extends and Generic Methods, WildCards - Upper Bound and Lower Bound.
- Introduction to Exception Handling - Your Thought Process during Exception Handling. try, catch and finally. Exception Hierarchy - Checked Exceptions vs Unchecked Exceptions. Throwing an Exception. Creating and Throwing a Custom Exception - CurrenciesDoNotMatchException. Try with Resources - New Feature in Java 7.

You will be using Eclipse and Brackets as the IDE. You will be using Maven, npm (Dependency Management), TestNG (XML Test Suite, Parallel, Multiple Browsers), JUnit, Selenium IDE, Katalon Studio, Selenium Standalone and Selenium Grid. We will help you set up each one of these.

- Tools : Maven, JUnit, TestNG (XML Test Suite, Groups, Listeners, Parallel, Multiple Browsers), Selenium IDE, Katalon Studio, Brackets
- Concepts : HTML, DOM, XPath, Selenium Architecture, Reporting (HTML), Parallel Execution (Data Driven Tests, Browsers, Test Ng, Grid), Debugging (Screenshots/logs), Page Object Model, Data Driven(Excel), Keyword Driven, Record and Replay, Selenium Grid, Cross Browser Testing, DRY
- Basics : Selenium Web Driver, Locating Web Elements(link text, name, id, xpath, css), Different Elements(select, radio, web tables, drag and drop, javascript alerts, windows, popups, iframes, switching windows), Wait (Explicit/Implicit), JavaScript Executor Action Class, Mouse movement, Keyboard with Selenium)
- Tips : Selenium Web Driver is an Interface, Headless Testing(PhantomJS, Chrome)
