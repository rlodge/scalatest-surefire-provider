[![Build Status](https://secure.travis-ci.org/TheLadders/scalatest-surefire-provider.png?branch=master)](http://travis-ci.org/TheLadders/scalatest-surefire-provider)

# ScalaTest Surefire Provider

Use ScalaTest with Surefire to execute JUnit/ScalaTest tests as part of a Maven build.

## What is a Surefire provider?
The Maven build tool uses a plugin called "Surefire" for running tests.  On its own Surefire knows nothing about
any one test framework.  Its job is to identify tests to be run and then report on the results.  Surefire relies
on "providers" to run the actual tests.  It ships with providers designed for running TestNG and JUnit tests.  Recently
the folks working on Surefire released a version allowing 3rd parties to implement their own providers.  This project is
a stab at creating a provider that uses ScalaTest as the test runner.

Integrating ScalaTest with Maven this way is clean and gives you some low level control over test
execution and the Maven build that would be hard if this was just a regular Maven plugin.

This provider is designed to be a drop-in replacement.  This means you can configure it the same way
as you configure the JUnit/TestNG providers, except for 1 or 2 key differences.  The default settings
are probably sufficient for most people.

## Quickstart
You need to add scalatest-surefire-provider as both a dependency and as a provider to the Surefire plugin (2 places).

The dependency will be something like this:

    <dependency>
      <groupId>com.theladders.platform</groupId>
      <artifactId>scalatest-surefire-provider</artifactId>
      <version>1.0</version>
    </dependency>

The provider config will be something like this (make sure you use maven-surefire-plugin version 2.11+):

    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-surefire-plugin</artifactId>
      <version>2.11</version>
      <dependencies>
        <dependency>
          <groupId>com.theladders.platform</groupId>
          <artifactId>scalatest-surefire-provider</artifactId>
          <version>1.0</version>
        </dependency>
      </dependencies>
    </plugin>

Most Maven projects that use Scala will want to use some other plugins too. If you're stuck try
looking at the "scalatest-surefire-provider-tests" project.  That pom.xml uses the plugin.


