<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <!-- Define project coordinates -->
    <groupId>com.example</groupId>
    <artifactId>my-struts2-webapp</artifactId>
    <version>1.0</version>
    <packaging>war</packaging> <!-- Packaging type for a web application -->

    <!-- Define project dependencies -->
    <dependencies>
        <!-- Struts 2 -->
        <dependency>
            <groupId>org.apache.struts</groupId>
            <artifactId>struts2-core</artifactId>
            <version>2.5.26</version> <!-- Adjust to your Struts 2 version -->
        </dependency>

        <!-- Servlet API (provided by servlet container) -->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
            <version>4.0.1</version> <!-- Adjust to your Servlet API version -->
            <scope>provided</scope> <!-- Provided scope for servlet container -->
        </dependency>

        <!-- Other dependencies for your project -->
    </dependencies>

    <!-- Build configuration -->
    <build>
        <sourceDirectory>src/main/java</sourceDirectory>
        <resources>
            <resource>
                <directory>src/main/resources</directory> <!-- Struts configuration files -->
            </resource>
        </resources>
        <plugins>
            <!-- Maven WAR plugin to package web application -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-war-plugin</artifactId>
                <version>3.2.3</version> <!-- Adjust to the appropriate version -->
                <configuration>
                    <!-- Configure web application-specific settings if needed -->
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>





<build>
    <!-- ... -->
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-war-plugin</artifactId>
            <version>3.2.3</version> <!-- Adjust to the appropriate version -->
            <configuration>
                <!-- Define web application-specific configurations here -->
            </configuration>
        </plugin>
        <!-- Other plugins you may need -->
    </plugins>
</build>










<build>
    <sourceDirectory>src</sourceDirectory> <!-- Java source files -->
    <resources>
        <resource>
            <directory>src</directory> <!-- Configuration files, if any -->
        </resource>
        <resource>
            <directory>WebContent</directory> <!-- JSP files and web-related resources -->
        </resource>
    </resources>
</build>





mvn install:install-file -Dfile=/path/to/your/custom.jar -DgroupId=com.example -DartifactId=custom-artifact -Dversion=1.0 -Dpackaging=jar






my-struts2-maven-project
├── src
│   ├── main
│   │   ├── java       (Java source files)
│   │   └── resources  (Configuration files)
│   └── test
│       ├── java       (Test source files)
│       └── resources  (Test configuration files)
├── target             (Generated output files)
├── WebContent         (JSP and web-related files)
├── pom.xml            (Maven project configuration)
└── ...

