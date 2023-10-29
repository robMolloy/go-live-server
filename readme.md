# http server

## initial global "go setup"

add go paths to `~/.zshrc` file

```
export GOPATH=$HOME/go
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```

# setup go module

run the following command

```
go mod init main.go
```

# install chi

run the following command

```
go get -u github.com/go-chi/chi/v5
```

which allow you to use the following code in your `main.go` file

```
package main

import (
    "net/http"

    "github.com/go-chi/chi/v5"
    "github.com/go-chi/chi/v5/middleware"
)

func main() {
    r := chi.NewRouter()
    r.Use(middleware.Logger)
    r.Get("/", func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte("Hello World!"))
    })
    http.ListenAndServe(":3000", r)
}
```

## Use air for hot reloading

install air globally with

```
go install github.com/cosmtrek/air@latest
```

run the following command to setup air with your project

```
air init
```

then use the following to enable your working project with hot reloading

```
air
```
