# GO实战：Web入门

## 1. 学习内容

本章我们学到了以下知识点：

- 如何创建 go 项目；
- 如何使用 VSCode 的内置命令行；
- 如何使用 go run 命令来运行 Go 程序；
- 如何使用 git 做版本控制；
- Go 应用中 package main 的规则；
- 标准库 fmt 包的基本使用；
- 标准库 http 包的基本使用；
- http 包中如何通过 url 路径来处理业务逻辑；
- 如何使用 air 来自动重载代码；
- 如何使用 go proxy 来加速 go get 命令；
- 如何添加 http 标头；
- 如何在不需要联网的情况下查看 Go 文档；
- 如何在 Go 文档中快速定位所需内容。

## 2.知识点总结

### 2.1如何创建go项目

- 一般会把项目放置在$GOPATH/src目录下
  - GOROOT是go根目录的环境变量
  - GOPATH是工作目录的环境变量
- 推荐目录是将Github用户名作为命名空间
  - 比如 $GOPATH/src/github.com/Ryan19929/goblog
  - main.go是程序的主入口

### 2.2 Go应用中package main的规则

- 存放 main 函数的文件名称不一定是 main.go，也可以是任何其他合规的 go 文件名称，例如 app.go、index.go。一般推荐使用 main.go，因为直观。
- 一个标准的可执行的 Go 程序必须有 package main 的声明。

### 2.3 标准库http包的基本使用

- Package http provides HTTP client and server implementations.
- ListenAndServe starts an HTTP server with a given address and handler. The handler is usually nil, which means to use DefaultServeMux. Handle and HandleFunc add handlers to DefaultServeMux:

```go
http.Handle("/foo", fooHandler)

// http.HandleFunc是向DefaultServeMux添加函数
http.HandleFunc("/bar", func(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "Hello, %q", html.EscapeString(r.URL.Path))
})

// ListenAndServe监听端口8080,第二个参数nil通常是默认DefaultServeMux
log.Fatal(http.ListenAndServe(":8080", nil)) 
```

- http.ResponseWriter: A ResponseWriter interface is used by an HTTP handler to construct an HTTP response.

```go
// 接口有一堆方法集
type ResponseWriter interface {
    Header() Header
    Write([]byte) (int, error)
    WriteHeader(statusCode int)
}
// Header有对应的方法
```

### 2.4 air来自动重载代码

- air是go的一个包-https://github.com/cosmtrek/air

### 2.5 go proxy和查看godoc

- ```she
  go env -w GOPROXY=https://goproxy.cn,direct
  ```

- ```she
  godoc -http=:6060
  ```

