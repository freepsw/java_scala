# java_scala
creating java and scala mixed project using intellij


## scala plugin need to be installd
> settings -> plugin -> available 탭에서 scala 검색 후 클릭해서 다운로드 설치.

## 1. Create project

 > File > New > Project > Maven 1.1 Add directory src/main/scala src/test/scala

##2. Edit pom.xml

```xml
    <groupId>com.freepsw</groupId>
    <artifactId>java_scala</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>jar</packaging>

    <dependencies>
        <dependency>
            <groupId>org.scala-lang</groupId>
            <artifactId>scala-library</artifactId>
            <version>2.11.8</version>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>net.alchim31.maven</groupId>
                <artifactId>scala-maven-plugin</artifactId>
                <executions>
                    <execution>
                        <id>scala-compile-first</id>
                        <phase>process-resources</phase>
                        <goals>
                            <goal>add-source</goal>
                            <goal>compile</goal>
                        </goals>
                    </execution>
                    <execution>
                        <id>scala-test-compile</id>
                        <phase>process-test-resources</phase>
                        <goals>
                            <goal>testCompile</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
```

추가된 directory의 색상이 java와 같은 색상으로 변하지 않을 경우, maven update를 해 주면 적용됨.
Intellij에서는

> File > Settings > Build,Execution,Deployment > Build Tools > Maven > Importing을 클릭
* Import Maven projects automatically 항목을 check

## 3. Create Scala Object adn Run

3.1 Create TestScala.scala
``` scala
object TestScala {
  def main(args: Array[String]) : Unit = {
    println("Helo Scala")
  }
}
```

3.2 click right button of mouse
"Run TestScala"가 보이면 성공.
