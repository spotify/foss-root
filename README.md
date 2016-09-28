# foss-root

A root pom for configuring common release related plugins for open source maven projects.

## Usage

There's still some boilerplate that has to go into your project `pom.xml`. Use the template below.

```xml
<project>
  <parent>
    <groupId>com.spotify</groupId>
    <artifactId>foss-root</artifactId>
    <version>1</version>
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
        <groupId>org.codehaus.mojo</groupId>
        <artifactId>license-maven-plugin</artifactId>
      </plugin>
      <plugin>
        <artifactId>maven-release-plugin</artifactId>
        <version>2.5.3</version>
      </plugin>
    </plugins>
  </build>
 </project>
```

After setting this up, you'll be able to


#### get license headers through

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
