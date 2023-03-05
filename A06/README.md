# maven使用心得
说一下这几年使用maven(mvnrepository.com)一些的心得.

## 获取所有的包来源
对特别服务大一些项目，特别是有多个同名不同版本的包，要怎么排除
mvn dependency:tree -Dverbose > target/tree.txt

## 怎样覆盖同名类
特别对于一些平台提供的对接包，常常存在需要修改里面的某个类的具体实现，或者对外提供一个jar包时，可以参考下这个方法
```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-dependency-plugin</artifactId>
    <version>3.5.0</version>
    <executions>
        <execution>
            <id>unpack</id>
            <phase>generate-sources</phase>
            <goals>
                <goal>unpack</goal>
            </goals>
            <configuration>
                <artifactItems>
                    <artifactItem>
                        <groupId>com.alibaba</groupId>
                        <artifactId>fastjson</artifactId>
                        <overWrite>false</overWrite>
                        <outputDirectory>${project.build.directory}/classes</outputDirectory>
                    </artifactItem>
                </artifactItems>
            </configuration>
        </execution>
    </executions>
</plugin>
```

## optional和scope的使用
对外提供一些基础功能时，对一些公共的依赖，大部分时候，不需要在基础包引入的，这时候可以使用optional和scope来配合
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <version>${spring.boot.version}</version>
    <optional>true</optional>
    <scope></scope>
</dependency>
```