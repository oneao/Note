## 创建项目
打开 Goland，点击 `New Project`，选择 `Go`，填写项目名称，点击 `Create` 创建工程。
![[Pasted image 20240810232431.png]]

## 新建`main.go`文件
在工程名称 `helloworld` 上右键，选择 `New`，选择 `Go File`，输入文件名称 `main`，回车。
![[Pasted image 20240810232455.png]]
添加以下代码
```go
package main

import "fmt"

func main() {
    fmt.Println("hello world!")
}
```
## 运行程序
1. 在 `main.go` 文件上右键，选择 `Run go build main.go`，即可运行程序。
2. 命令行运行
```go
go run main.go
```

