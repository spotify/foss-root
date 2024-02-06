# foss-root

A root pom for configuring common release related plugins for open source maven projects.

## Usage

There's still some boilerplate that has to go into your project `pom.xml`. Use the template below.

```xml

<project>
  <parent>
    <groupId>com.spotify</groupId>
    <artifactId>foss-root</artifactId>
    <version>LATEST-VERSION</version>
  </parent>

  <artifactId>YOUR_ARTIFACT_NAME</artifactId>
  <version>VERSION-SNAPSHOT</version>

  <licenses>
    <license>
      <name>The Apache Software License, Version 2.0</name>
      <url>http://www.apache.org/licenses/LICENSE-2.0.txt</url>
      <distribution>repo</distribution>
    </license>
  </licenses>

  <developers>
    <developer>
      ...
    </developer>
  </developers>

  <scm>
    <url>https://github.com/spotify/YOUR_REPO</url>
    <connection>scm:git:git@github.com:spotify/YOUR_REPO.git</connection>
    <developerConnection>scm:git:git@github.com:spotify/YOUR_REPO.git</developerConnection>
    <tag>HEAD</tag>
  </scm>

  <build>
    <plugins>
      <plugin>
        <artifactId>maven-checkstyle-plugin</artifactId>
      </plugin>
      <plugin>
        <artifactId>maven-enforcer-plugin</artifactId>
      </plugin>
      <plugin>
        <artifactId>maven-failsafe-plugin</artifactId>
      </plugin>
    </plugins>
  </build>
</project>
```

By default your project will target Java 8. If you don't need Java 8 compatibility and you would like to target a later version of Java, set the
`java.version` property in your project, like so:

```xml

<properties>
  <java.version>11</java.version>
</properties>
```

After setting this up, you'll be able to

#### add license headers to all sources

```
mvn license:update-file-header
```

#### deploy snapshots

```
mvn deploy
```

#### deploy releases

```
mvn release:prepare
mvn release:perform
``` 

#### Fail if no tests

By default, from version 16+ any project using `foss-root` will fail if there are not unit-tests.

You can override this behaviour by setting the property `unitTests.failIfNoTests` equal to `false`.

An equivalent `integrationTests.failIfNoTests` exists, but its default is set to `false`.
