# 源码调试步骤
## 1.tomcat官方网站下载core和source代码
## 2.在指定目录创建一个文件夹，比如tomcat，把下载的core和source解压放到创建好的文件夹中
## 3.在tomcat目录下创建pom.xml文件，内容如下
```
<?xml version="1.0" encoding="UTF-8"?>    
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"    
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">    
    
    <modelVersion>4.0.0</modelVersion>    
    <groupId>org.apache</groupId>    
    <artifactId>tomcat</artifactId>    
    <name>tomcat</name>    
    <version>1.0</version>    
    <packaging>pom</packaging>    
    
    <modules>    
        <module>apache-tomcat-8.5.93-src</module>
    </modules>    
</project>
```
在source文件创建pom文件
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  
    <modelVersion>4.0.0</modelVersion>
    <groupId>org.apache.tomcat</groupId>
    <artifactId>Tomcat8.0</artifactId>
    <name>Tomcat8.0</name>
    <version>8.0</version>

    <build>
        <finalName>Tomcat8.0</finalName>
        <sourceDirectory>java</sourceDirectory>
        <testSourceDirectory>test</testSourceDirectory>
        <resources>
            <resource>
                <directory>java</directory>
            </resource>
        </resources>
        <testResources>
            <testResource>
                <directory>test</directory>
            </testResource>
        </testResources>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>2.0.2</version>

                <configuration>
                    <encoding>UTF-8</encoding>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>

    <dependencies>
        <dependency>
            <groupId>ant</groupId>
            <artifactId>ant</artifactId>
            <version>1.7.0</version>
        </dependency>
        <dependency>
            <groupId>ant</groupId>
            <artifactId>ant-apache-log4j</artifactId>
            <version>1.6.5</version>
        </dependency>
        <dependency>
            <groupId>ant</groupId>
            <artifactId>ant-commons-logging</artifactId>
            <version>1.6.5</version>
        </dependency>
        <dependency>
            <groupId>wsdl4j</groupId>
            <artifactId>wsdl4j</artifactId>
            <version>1.6.2</version>
        </dependency>
        <dependency>
            <groupId>javax.xml.rpc</groupId>
            <artifactId>javax.xml.rpc-api</artifactId>
            <version>1.1</version>
        </dependency>
        <dependency>
            <groupId>org.eclipse.jdt.core.compiler</groupId>
            <artifactId>ecj</artifactId>
            <version>4.6.1</version>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>
      
      <!-- https://mvnrepository.com/artifact/org.easymock/easymock -->
      <dependency>
        <groupId>org.easymock</groupId>
        <artifactId>easymock</artifactId>
        <version>4.3</version>
        <scope>test</scope>
      </dependency>

      <!-- https://mvnrepository.com/artifact/com.unboundid/unboundid-ldapsdk -->
      <dependency>
        <groupId>com.unboundid</groupId>
        <artifactId>unboundid-ldapsdk</artifactId>
        <version>5.1.4</version>
        <scope>test</scope>
      </dependency>
    </dependencies>
</project>
```
## 4.添加VM 参数 -Dcatalina.home="/Users/hassan/develop/project/java-project/tomcat/apache-tomcat-8.5.93" 注意这里是VM 参数，不是program argument参数。