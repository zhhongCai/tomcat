### 如何导入到IDEA

#### 下载源码

```bash
    git clone https://github.com/zhhongCai/tomcat.git
```                                                  

#### 确保系统已安装JDK1.8（或以上版本），ant


#### CD到tomcat根目录：

修改build.properties.default

```properties
    # 增加属性 
    # Code signing of Windows installer
    skip.installer=true

    # 修改依赖库路径，编译时自动下载依赖包到这个目录下
    # contexts by the various build scripts.
    base.path=${user.home}/tomcat-build-libs
```

执行命令
 
```bash
    ant ide-intellij  
    ant release
``` 

#### IDEA导入tomcat源码

项目属性增加依赖包

#### 运行Bootstrap,启动tomcat

配置启动参数：

```text
     #VM options
     #TOMCAT_SOURCE_HOME=tomcat源码根目录(ant release执行成功后生成)

    -Dcatalina.home=${TOMCAT_SOURCE_HOME}/output/dist
    -Dcatalina.base=${TOMCAT_SOURCE_HOME}/output/dist
    -Djava.io.tmpdir=${TOMCAT_SOURCE_HOME}/output/dist/temp
    -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager
    -Djava.util.logging.config.file=${TOMCAT_SOURCE_HOME}/output/dist/conf/logging.properties

```