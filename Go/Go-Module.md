# Go module

## 1. Access
- In Go, a function whose name starts with a capital letter, can be called by a function not in the same package.
- It means any "unexported" names are not accessible from outside the package.

## 2. What is a module

### 2.1 Introduction
- Module are how Go manages dependencies.
- https://golang.org/ref/mod#go-mod-file

### 2.2 Module, package, and versions
- Module: a collection of packages that are released, versioned, and distributed together.
- A module is identified by a module path, which is declared in a go.mod file, together with information about the module's dependencies.
- A package's path is what the module's path added the name of packages.
### 2.3 Module path
- Tell people what module do and where to find it.
- Typically, a module path consist of a repository root path, a directory with the repository(usually empty), and a major version suffix(only for major version 2 or higher)

## 3. go.mod files
### 3.1 What is go.mod
- A module is defined by a UTF-8 encoded text file named go.mod in its root directory.
- The go.mod file is lineoriented. Each line holds a single directive, made uo of  a keyword followed by arguments.
```Go
module example.com/my/thing

go 1.12

require example.com/other/thing v1.0.2
require example.com/new/thing/v2 v2.3.4
exclude example.com/old/thing v1.2.3
replace example.com/bad/thing v1.4.5 => example.com/good/thing v1.4.5
retract [v1.9.0, v1.9.5]
```
- Using go get can automatically update the go.mod file. 