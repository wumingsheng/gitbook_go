# imooc商品详情页案例


1. 使用beego的命令工具，创建一个项目`bee new imooc-demo`
2. 发现beego里面用到一个测试框架`GoConvey`，需要安装`$ https_proxy=socks5://127.0.0.1:1080 go get github.com/smartystreets/goconvey`
3. 直接运行main文件，发现找不多静态模版文件，是因为`go run main.go`命令不加载静态文件，需要先`go build`,在执行`./app`




