#### 1.项目导入|打开IDEA，选择import Project；或者在已经打开的IDEA项目界面选择File - New - Project from Existing Source…；

![[开发工具/IDEA/imgs/1.png]]

#### 2.项目导入 | 在弹出的Select File or Directory to import框里选择你要导入的eclipse web项目源文件（这里要导入的是AirPort）
![[开发工具/IDEA/imgs/2.png]]

#### 3.项目导入 | 下面无需更多的操作，一路 Next 就可以了
![[开发工具/IDEA/imgs/3.png]]

![[Pasted image 20240810145708.png]]

![[Pasted image 20240810145717.png]]

![[Pasted image 20240810145726.png]]

![[Pasted image 20240810145736.png]]

这里是选择导入的此项目运行的环境，这里JDK版本默认选择1.8，指定jdk路径

![[Pasted image 20240810145747.png]]

最后点击 Finish,这个项目到此就已导入完成
![[Pasted image 20240810145805.png]]

#### 4.项目配置 | 打开File - Project Structure 或者点击设置图标，选择Artifacts，点击 “+” 号
![[Pasted image 20240810145817.png]]

![[Pasted image 20240810145823.png]]

![[Pasted image 20240810145842.png]]

![[Pasted image 20240810145854.png]]

#### 5.项目配置 | 按照图示选择Archive - For *******

![[Pasted image 20240810145900.png]]

![[Pasted image 20240810145906.png]]

#### 6.Tomact 配置 | 选择 Add Configuration… - “+” - Tomcat Server - Local 进行 tomcat 配置 （如图）
![[Pasted image 20240810145922.png]]

#### 7.Tomcat 配置 | 进入配置页面首页选择Deployment - 下面“+”号，然后选择Artifacet（指定Tomcat 编译项目）
![[Pasted image 20240810145929.png]]

选择第一个编译文件
![[Pasted image 20240810145940.png]]

下面Application context 中填写的是运行项目后，访问项目是否需要在连接中填写项目名称，这里默认设置。(也可设置为AirPort，比如若是在web根目录下有index.jsp，那么路径为http://localhost:8080/index.jsp，而不是http://localhost:8080/AirPort/index.jsp)。
![[Pasted image 20240810145948.png]]

#### 8.Tomcat配置 | 然后点击 Server 进入tomcat的详情配置页面；

Name是tomcat的在项目中的别名（这里直接以端口号命名的）；
Application server 中选择tomcat版本，如果没有要选择的可以在后面Configure...中配置，这里不做过多的说明；
Open browser是项目启动后自动打开的浏览器；
URL是自动打开浏览器后访问的连接，默认是勾选的；
JRE 是选择指定的JDK，idea有默认指定的jdk（这里是根据个人习惯选择本地的jdk，此处的jdk会和之前操作的JDK版本相对应，如果版本不一致会报错）点击OK,配置完成。
![[Pasted image 20240810150014.png]]