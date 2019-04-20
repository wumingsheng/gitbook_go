# RESTful路由

`go get` 安装beego

```go
package main

import (
	"fmt"
	"github.com/astaxie/beego"
)

type TestController struct {
	beego.Controller
}

func (this *TestController) Get() {

	this.Ctx.WriteString("hello test in GET method")

}

func (this *TestController) Post() {

	this.Ctx.WriteString("hello test in POST method")

}

type RegExpController struct {
	beego.Controller
}

func (this *RegExpController) Get() {

	this.Ctx.WriteString(fmt.Sprintln("this is RegExp request"))
	id := this.Ctx.Input.Param(":id")
	this.Ctx.WriteString(fmt.Sprintf("=== id is %s\n", id))

}

type GenericController struct {
	beego.Controller
}

func (this *GenericController) Get() {
	this.Ctx.WriteString("===GenericController...")
	splat := this.Ctx.Input.Param(":splat")
	path := this.Ctx.Input.Param(":path")
	ext := this.Ctx.Input.Param(":ext")
	this.Ctx.WriteString(fmt.Sprintf("splat is %s, path is %s, ext is %s\n", splat, path, ext))

}

func main() {

	//restfule route
	beego.RESTRouter("/test", &TestController{})

	//regex route
	beego.Router("/regex1/?:id", &RegExpController{})
	//regex match for numbers only
	beego.Router("/regex2/:id([0-9]+)", &RegExpController{})
	//regex match for str only
	beego.Router("/regex3/:id([\\w]+)", &RegExpController{})

	// regex match *
	beego.Router("/regex4/*", &GenericController{})
	beego.Router("/regex5/*.*", &GenericController{})

	beego.Run("127.0.0.1:8080")

}

```

