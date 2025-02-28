## 添加国内镜像源
在`gradle-x.x/init.d`文件夹下添加文件`init.gradle`
```bash
sudo nano init.gradle
```
添加以下内容
```kotlin
allprojects {
    repositories { 
        mavenLocal() 
        maven { name "Alibaba" ; url "https://maven.aliyun.com/repository/public" } 
        maven { name "Bstek" ; url "https://nexus.bsdn.org/content/groups/public/" } 
        mavenCentral()
    }
    buildscript {
        repositories { 
            maven { name "Alibaba" ; url 'https://maven.aliyun.com/repository/public' } 
            maven { name "Bstek" ; url 'https://nexus.bsdn.org/content/groups/public/' } 
            maven { name "M2" ; url 'https://plugins.gradle.org/m2/' }
        }
    }
}
```
## 配置IDEA
选择`Settings -> Build -> Build Tools -> Gradle`
其中`Gradle user home`可默认
![[自动化构建工具/Gradle/Images/1.png]]
>Windows系统同理。
