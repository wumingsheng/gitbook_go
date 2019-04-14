# Introduction



## go get 配置代理

go get 的时候会执行两个步骤：

1. clone源代码到`$GOPATH/src`下
2. （-u 参数）安装install可执行文件到`$GOPATH/bin`目录下

clone代码使用的是`git clone`命令，有时候由于网络原因，`go get`会失败

可以配置代理，让`go get`命令顺利执行

### 方式一：通过shell代理

临时生效，关闭终端 `export` 的环境变量就没有了，要想永久生效就要配置到环境变量配置文件里面

```bash

$ export http_proxy=socks5://127.0.0.1:1080
$ export https_proxy=socks5://127.0.0.1:1080

```

### 方式二：通过git代理设置

```bash

$ git config --global http.proxy socks5://127.0.0.1:1080
$ git config --global https.proxy socks5://127.0.0.1:1080
$ git config --global --unset http.proxy
$ git config --global --unset https.proxy


```

### 方式三：只为当前命令生效

```bash

$ https_proxy=socks5://127.0.0.1:1080 go get -u github.com/beego/bee

```



