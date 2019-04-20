# RESTful路由


## router

```go
package main

import (
	"fmt"
	"github.com/gin-gonic/gin"
	"net/http"
)

func main() {

	router := gin.Default()

	//restful get router
	router.GET("/helloWorld", helloWorld)

	// restful post router
	router.POST("hello-post", helloPost)
	// not support regex express
	//parse path'params
	router.GET("pathParam/:id", pathParam)
	// group router
	group1 := router.Group("/g1")

	//gin'group default writing style
	{
		group1.GET("/h1", h1)
		group1.GET("/h2", h2)
	}

	//server start
	router.Run("127.0.0.1:8080")

}

func h2(context *gin.Context) {
	context.String(http.StatusOK, "return h2")
}

func h1(context *gin.Context) {
	context.String(http.StatusOK, "return h1")
}

func pathParam(context *gin.Context) {
	id := context.Param("id")
	context.String(http.StatusOK, fmt.Sprintf("id is %s\n", id))
}

// RESTFUL ROUTER GET FUNC
func helloPost(context *gin.Context) {
	context.String(http.StatusOK, "HELLO GIN! POST METHOD")
}

// RESTFUL ROUTER POST FUNC
func helloWorld(context *gin.Context) {
	context.String(http.StatusOK, "HELLO GIN, Get method")
}

```


