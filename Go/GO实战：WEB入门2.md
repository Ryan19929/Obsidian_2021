# Secnd
- Keywords: Router, Go Module, Middleware

## 1.Router
- 处理HTTP请求主要是ServerMux和Handler
- ServerMux中的Mux是多路复用器，起到的作用就是将受到的请求与预先定义的URL作对比，在匹配后调用相关的处理器Handler
- http.HandleFunc()是对DefaultServeMux.HandleFunc()的封装
- http.ListenAndServe(), 第二个参数为空时，使用默认的ServerMux
### 1.1 Other Router
- gorilla/mux: 功能丰富
- HttpRouter->gin: 功能简单但是性能好

## 2.Go Module
- GO Module 是从1.11版本开始使用的官方的包管理工具
### 2.1 命令
- go mod init
- go mod tidy
- go get -u xxxxxx/xxx
### 2.2go.mod file
[[Go-Module#3 go mod files|learn go.mod file ]]

## 3.Middleware
- Middleware是可以用来作一些统一的相应，现经过中间件在按顺序走。      