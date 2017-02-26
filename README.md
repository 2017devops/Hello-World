# pipeline-as-code-demo

Check the dependency version and update

Add Maven version plugin in pom.xml

<plugin>
      		<groupId>org.codehaus.mojo</groupId>
      		<artifactId>versions-maven-plugin</artifactId>
      		<version>2.3</version>
</plugin>

mvn versions:set -DgroupId=com.google.guava -DartifactId=guava -DoldVersion=12.0 -DnewVersion=2.1.0
