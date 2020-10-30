# AERIUS Tools

This repository contains configuration and setup files for the development environment of AERIUS products.

## Eclipse

In `src/main/resources` a number of Eclipse configuration files are available.
These files can be imported in Eclipse to correctly set the AERIUS coding style.

## Spotless

This project contains the configuration for automatic code formatting using Spotless.
To use Spotless with AERIUS projects add the following in the `pom.xml` in `pluginManagement`:

```
  <plugin>
    <groupId>com.diffplug.spotless</groupId>
    <artifactId>spotless-maven-plugin</artifactId>
    <version>${spotless.version}</version>
    <configuration>
      <formats>
        <format>
          <includes>
            <include>pom.xml</include>
          </includes>
          <licenseHeader>
            <file>pom-xml-header.txt</file>
            <delimiter>&lt;project</delimiter>
          </licenseHeader>
          <trimTrailingWhitespace />
          <endWithNewline />
          <eclipseWtp>
            <type>XML</type>
            <files>
              <file>pom-xml.prefs</file>
            </files>
           </eclipseWtp>
        </format>
      </formats>
      <java>
        <includes>
          <include>src/*/java/nl/overheid/aerius/**/*.java</include>
        </includes>
        <licenseHeader>
          <file>checkstyle-header.txt</file>
        </licenseHeader>
        <eclipse>
          <file>eclipse_code_formatter_profile.xml</file>
        </eclipse>
        <importOrder>
          <file>eclipse.importorder</file>
        </importOrder>
      </java>
    </configuration>
    <dependencies>
      <dependency>
        <groupId>nl.aerius</groupId>
        <artifactId>tools</artifactId>
        <version>1.0.0</version>
      </dependency>
    </dependencies>
  </plugin>
```

The tools jar is found in the AERIUS nexus repository.
Add the following to the `pom.xml`

```
  <pluginRepositories>
    <pluginRepository>
      <id>aerius-nexus-public</id>
      <name>AERIUS Nexus Repository</name>
      <url>https://nexus.aerius.nl/repository/maven-public/</url>
    </pluginRepository>
  </pluginRepositories>
```

Spotless can be run with maven.
Either by checking `mvn spotless:check` or by automatically correcting with `mvn spotless:apply`.
