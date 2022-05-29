# Golang

## Setup

```
go mod init mymodule

go install -v golang.org/x/tools/gopls@latest
go install -v github.com/ramya-rao-a/go-outline@latest
```

## Filetree

```
projects
        mymodule
                mpkg
                        utils.go
                go.mod
                main.go
```

## main.go

```go
package main

import (
	"fmt"
	"log"
	"net/http"
	"mymodule/mpkg"   // Example of import
	"time"
)

func getRoot(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "getRoot!")
}

func getHello(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "getHello!")
}

func main() {
	log.SetFlags(0)
	log.Println("Starting server at port 8080")

	mpkg.PrintHello()

	mux := http.NewServeMux()
	mux.HandleFunc("/", getRoot)
	mux.HandleFunc("/hello", getHello)

	s := http.Server{
		Addr:           ":8080",
		Handler:        mux,
		ReadTimeout:    10 * time.Second,
		WriteTimeout:   10 * time.Second,
		MaxHeaderBytes: 1 << 20,
	}

	err := s.ListenAndServe()
	if err != nil {
		log.Fatal(err)
	}
}
```
