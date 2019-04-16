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


## 搭建 go 开发环境

首先我想说的是 我心里也有一万头草泥马在狂奔

折腾了半天sublime搭建go环境,效果是有 很麻烦 本着简单第一免费的原则, 还是用vscode

1. 首先是下载go安装包
2. 解压 tar -C /usr/local -xzf go1.12.1.linux-amd64.tar.gz
3. 配置环境变量,查看是否配置成功 go version

	GOROOT=/usr/local/go
	GOPATH=/home/user/go

	PATH=$PATH:$GOROOT/bin:$GOPATH/bin
	export GOROOT GOPATH PATH

4. vscode安装go插件和工具

	安装的go插件是go,code runner
	随便打开一个go文件,vscode自动推荐安装工具,选择了install all 但是基本上大部分下载不下来

5. 手动下载

	mkdir -p $GOPATH/src/golang.org/x
	cd /home/user/go/src/golang.org/x
	git clone https://github.com/golang/tools.git
	git clone https://github.com/golang/lint.git 

	Installing github.com/mdempsky/gocode FAILED
	Installing github.com/stamblerre/gocode FAILED

	go install github.com/ramya-rao-a/go-outline
	go install golang.org/x/tools/cmd/guru
	go install github.com/sqs/goreturns
	go install github.com/acroca/go-symbols
	go install golang.org/x/tools/cmd/gorename
	go install golang.org/x/lint/golint

	重启了vscode自动完成了安装gocode

6. 开始code



