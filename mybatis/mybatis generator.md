## mybatis generator

http://www.cnblogs.com/yjmyzz/p/4210554.html

[mybatis-generator](https://github.com/mybatis/generator)有三种用法：命令行、eclipse插件、maven插件。个人觉得maven插件最方便，可以在eclipse/intellij idea等ide上可以通用。

带界面版的mybatis geneator，[https://github.com/astarring/mybatis-generator-gui](https://github.com/astarring/mybatis-generator-gui)

下面是从官网上的截图：(不过官网[www.mybatis.org](http://www.mybatis.org) 最近一段时间,好象已经挂了)

![img](http://images.cnitblog.com/blog/27612/201501/081227432658706.png)

一、在pom.xml中添加plugin

```java
<plugin>
    <groupId>org.mybatis.generator</groupId>
    <artifactId>mybatis-generator-maven-plugin</artifactId>
    <version>1.3.2</version>
    <configuration>
        <configurationFile>src/main/resources/mybatis-generator/generatorConfig.xml</configurationFile>
        <verbose>true</verbose>
        <overwrite>true</overwrite>
    </configuration>
    <executions>
        <execution>
            <id>Generate MyBatis Artifacts</id>
            <goals>
                <goal>generate</goal>
            </goals>
        </execution>
    </executions>
    <dependencies>
        <dependency>
            <groupId>org.mybatis.generator</groupId>
            <artifactId>mybatis-generator-core</artifactId>
            <version>1.3.2</version>
        </dependency>
    </dependencies>
</plugin>
```

其中generatorConfig.xml的位置，大家根据实际情况自行调整

二、generatorConfig.xml配置文件

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE generatorConfiguration
        PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
        "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">

<generatorConfiguration>
    <classPathEntry
            location="C:/Oracle/Middleware/wlserver_10.3/server/lib/ojdbc6.jar"/>
    <context id="my" targetRuntime="MyBatis3">
        <commentGenerator>
            <property name="suppressDate" value="false"/>
            <property name="suppressAllComments" value="true"/>
        </commentGenerator>

        <jdbcConnection driverClass="oracle.jdbc.driver.OracleDriver"
                        connectionURL="jdbc:oracle:thin:@172.20.16.***:1521:CARGO" userId="***"
                        password="***"/>

        <javaModelGenerator targetPackage="ctas.test.entity"
                            targetProject="D:/yangjm/Code/CTAS/JAVAEE/CTAS2CCSP/src/main/java">
            <property name="enableSubPackages" value="true"/>
            <property name="trimStrings" value="true"/>
        </javaModelGenerator>

        <sqlMapGenerator targetPackage="ctas.test.entity.xml"
                         targetProject="D:/yangjm/Code/CTAS/JAVAEE/CTAS2CCSP/src/main/java">
            <property name="enableSubPackages" value="true"/>
        </sqlMapGenerator>

        <javaClientGenerator targetPackage="ctas.test.mapper"
                             targetProject="D:/yangjm/Code/CTAS/JAVAEE/CTAS2CCSP/src/main/java" type="XMLMAPPER">
            <property name="enableSubPackages" value="true"/>
        </javaClientGenerator>

        <!--<table tableName="T_FEE_AGTBILL" domainObjectName="FeeAgentBill"
               enableCountByExample="false" enableUpdateByExample="false"
               enableDeleteByExample="false" enableSelectByExample="false"
               selectByExampleQueryId="false"/>-->

        <table tableName="CTAS_FEE_BASE" domainObjectName="FeeBase"
               enableCountByExample="false" enableUpdateByExample="false"
               enableDeleteByExample="false" enableSelectByExample="false"
               selectByExampleQueryId="false">
            <!--<columnRenamingRule searchString="^D_"
                                replaceString=""/>-->
        </table>

    </context>
</generatorConfiguration>
```

几个要点：
a) 因为生成过程中需要连接db，所以第3行指定了驱动jar包的位置

b) 15-17行为连接字符串

c) 19-33行指定生成“entity实体类、mybatis映射xml文件、mapper接口”的具体位置

d) 40-46行为具体要生成的表，如果有多个表，复制这一段，改下表名即可

 

三、使用方式

mvn mybatis-generator:generate

如果是在intellij 环境，直接鼠标点击即可

![img](http://images.cnitblog.com/blog/27612/201501/081223382503659.jpg)

 

最后给出目录结构图：

![img](http://images.cnitblog.com/blog/27612/201501/081226229375280.jpg)

最后给一些小技巧：

a) 建表时，字段名称建议用"_"分隔多个单词，比如:AWB_NO、REC_ID...，这样生成的entity，属性名称就会变成漂亮的驼峰命名，即：awbNo、recId

b)oracle中，数值形的字段，如果指定精度，比如Number(12,2)，默认生成entity属性是BigDecimal型 ，如果不指定精度，比如:Number(9)，指默认生成的是Long型

c)oracle中的nvarchar/nvarchar2，mybatis-generator会识别成Object型，建议不要用nvarchar2，改用varchar2