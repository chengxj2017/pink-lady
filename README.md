# pink-lady

![proj-icon](https://raw.githubusercontent.com/axiaoxin/pink-lady/master/misc/pinklady.png)

[![Build Status](https://travis-ci.org/axiaoxin/pink-lady.svg?branch=master)](https://travis-ci.org/axiaoxin/pink-lady)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/b906dd1655074f60bf93a7c592d29204)](https://www.codacy.com/app/axiaoxin/pink-lady?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=axiaoxin/pink-lady&amp;utm_campaign=Badge_Grade)
[![go report card](https://goreportcard.com/badge/github.com/axiaoxin/pink-lady)](https://goreportcard.com/report/github.com/axiaoxin/pink-lady)
[![codecov](https://codecov.io/gh/axiaoxin/pink-lady/branch/master/graph/badge.svg)](https://codecov.io/gh/axiaoxin/pink-lady)
![version-badge](https://img.shields.io/github/release/axiaoxin/pink-lady.svg)
![downloads](https://img.shields.io/github/downloads/axiaoxin/pink-lady/total.svg)
![license](https://img.shields.io/github/license/axiaoxin/pink-lady.svg)
![issues](https://img.shields.io/github/issues/axiaoxin/pink-lady.svg)
[![Say Thanks!](https://img.shields.io/badge/Say%20Thanks-!-1EAEDB.svg)](https://saythanks.io/to/axiaoxin)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/axiaoxin/pink-lady/pulls)

The typically [gin](https://github.com/gin-gonic/gin)-based web application's organizational structure -> pink-lady.

The name comes from the Pink Lady which is a national standard cocktail with Gin as Base.

## Skeleton code organization structure

    > tree -I "vendor"
    .
    ├── app                                          // source code directory
    │   ├── apis                                    // write your apis at this directory
    │   │   ├── init.go                            // skeleton default api
    │   │   ├── init_test.go
    │   │   ├── router                             // gin router
    │   │   │   ├── router.go
    │   │   │   └── router_test.go
    │   │   ├── routes.go                          // register your handler function on url in here
    │   │   └── routes_test.go
    │   ├── app.yaml                                // configuration file
    │   ├── docs                                    // api docs generate by swag
    │   │   ├── docs.go
    │   │   └── swagger
    │   │       ├── swagger.json
    │   │       └── swagger.yaml
    │   ├── main.go                                 // main run a endless api server
    │   ├── middleware                              // skeleton default middlewares
    │   │   ├── errorhandler.go                    // handle 404 500 to return JSON
    │   │   ├── errorhandler_test.go
    │   │   ├── ginlogrus.go                       // logs use logrus
    │   │   ├── ginlogrus_test.go
    │   │   ├── init.go
    │   │   ├── requestid.go                       // log request id
    │   │   └── requestid_test.go
    │   ├── models                                  // write your models at here
    │   │   ├── init.go                            // provide a base model
    │   │   └── init_test.go
    │   ├── services                                // write your business handler at here
    │   │   ├── init.go
    │   │   ├── init_test.go
    │   │   └── retcode                            // write your business return code at here
    │   │       ├── retcode.go
    │   │       └── retcode_test.go
    │   └── utils                                   // add common utils at here
    │       ├── endless.go                          // provide a graceful stop server
    │       ├── gorequest.go                        // provide a http client
    │       ├── gorm.go                             // provide gorm db client
    │       ├── gorm_test.go
    │       ├── init.go
    │       ├── jsontime.go                         // provide a custom format time field for json
    │       ├── jsontime_test.go
    │       ├── logrus.go                           // provide a log
    │       ├── logrus_test.go
    │       ├── pagination.go                       // provide a pagination function
    │       ├── pagination_test.go
    │       ├── redis.go                            // provide a redis client
    │       ├── redis_test.go
    │       ├── response                            // provide united json response functions
    │       │   ├── response.go
    │       │   └── response_test.go
    │       ├── testing.go                          // provide GET/POST request function for testing
    │       ├── viper.go                            // provide configuration parser
    │       └── viper_test.go
    ├── Gopkg.lock                                   // dep file
    ├── Gopkg.toml                                   // dep file
    ├── misc                                         // write your tool scripts at here
    │   ├── pre-push.githook                        // a git pe-push hook for run test when push
    │   ├── README.md
    │   ├── release.sh                              // a tool for release the binary app
    │   └── supervisor.conf                         // a supervisor configure file demo
    └── README.md

## Develop requirements

- **[[Go >= 1.10]](https://golang.org/doc/devel/release.html)** It requires Go 1.10 or newer to use dep and run testing coverage.
- **[[golang/dep]](https://github.com/golang/dep)** Go dependency management tool <https://golang.github.io/dep/>
- **[[swaggo/swag]](https://github.com/swaggo/swag)** Automatically generate RESTful API documentation with Swagger 2.0 for Go.
- **[[pilu/fresh]](https://github.com/pilu/fresh)** Build and (re)start go web apps after saving/creating/deleting source files.

You maybe need to install them. For installation, please refer to their home page.

## Skeleton dependencies

- **[[spf13/viper]](https://github.com/spf13/viper)** Go configuration with fangs
- **[[sirupsen/logrus]](https://github.com/sirupsen/logrus)** Structured, pluggable logging for Go.
- **[[fvbock/endless]](https://github.com/fvbock/endless)** Zero downtime restarts for go servers (Drop in replacement for http.ListenAndServe)
- **[[jinzhu/gorm]](https://github.com/jinzhu/gorm)** The fantastic ORM library for Golang, aims to be developer friendly <http://gorm.io>
- **[[satori/go.uuid]](https://github.com/satori/go.uuid)** UUID package for Go
- **[[go-redis/redis]](https://github.com/go-redis/redis)** Type-safe Redis client for Golang <https://godoc.org/github.com/go-redis/redis>
- **[[swaggo/gin-swagger]](https://github.com/swaggo/gin-swagger)** gin middleware to automatically generate RESTful API documentation with Swagger 2.0.
- **[[gin-contrib/cors]](https://github.com/gin-contrib/cors)** Official CORS gin's middleware
- **[[gin-contrib/sentry]](https://github.com/gin-contrib/sentry)** Middleware to integrate with sentry crash reporting.
- **[[alicebob/miniredis]](https://github.com/alicebob/miniredis)** Pure Go Redis server for Go unittests
- **[[parnurzeal/gorequest]](https://github.com/parnurzeal/gorequest)** GoRequest -- Simplified HTTP client ( inspired by nodejs SuperAgent ) <http://parnurzeal.github.io/gorequest/>

## Feature

- Clear code organization.
- Validation of production environment.
- Flexible and rich configuration, easy to configure for server, log, database, redis and sentry.
- Detailed and leveled log, easy to log gin request log with requestid and orm sql log.
- Support multiple database ORM such as sqlite3, mysql, postgresql and sqlserver.
- Support redis single client, sentinel client and cluster client.
- Support sentry for collecting panic logs.
- Provide a graceful restart/stop server.
- Integration of gorequest, pagination, functions for testing and other common tools.
- Provide functions to respond unified JSON structrue with `code`, `message`, `data` fields.
- Provide easy-to-use business return code.
- Gin router support handle 404/500 requests as a unified JSON structure.
- Support auto generating the swagger API docs by comments
- Provide a `release.sh` tool for releasing binary in `misc` directory.

## How to build web API server with pink-lady

First, Clone the pink-lady into your gopath and install dependebcies:

    cd $(go env GOPATH)/src
    mkdir -p github.com/axiaoxin
    cd github.com/axiaoxin
    git clone git@github.com:axiaoxin/pink-lady.git
    cd pink-lady

the vendor directory contain the dependencies, if not, install them by:

    dep ensure

if you need use new dependencies, you should run the cmd before write code:

    dep ensure --add xxxxxxxx

if you want to change the project path or name, you must change the import path too:

    mv github.com/axiaoxin/pink-lady XXX/YYY/ZZZ
    cd XXX/YYY/ZZZ/app
    sed -i  "s|github.com/axiaoxin/pink-lady|XXX/YYY/ZZZ|g"  `grep "github.com/axiaoxin/pink-lady" . -rl`

Second, Write your API in `apis` directory, you can create a file or a subdirectory as a package to save your gin API handler function, then register the handlers on url in `apis/routes.go` like the default `ping` API

Third, Run develop server in `app` directory:

    cd app
    go test ./...
    go run main.go

Fourth, Release your API server, run `misc/release.sh` will build a binary app in `build` directory if your tests all pass, and bump version, update api docs and make a git commit and add a tag with the version

    cd misc
    ./release.sh

If you wrote swag style comments you can generate the API docs in `app` directory manually:

    cd app
    swag init -g apis/init.go

You can test your API by curl or swagger API docs:<http://pink-lady:4869/x/apidocs/index.html>, sure, you need to configure a host of pink-lady for your server

## Develop suggestions

- You should put your API handler functions in `app/apis` as a single file or a package, then register the handlers in `app/apis/routes.go`
- Add your middleware in `app/middleware`, use it by adding to `app/apis/router/router.go`
- Define the database model in `app/models` by embed `BaseModel` in `app/models/init.go`
- Write reusable business code in `app/services` as single file or a package
- Define the return codes in `app/services/retcode/retcode.go`
- Add generic business independent tool type code in `app/utils`
- Add tool scripts etc in `misc`
- Write unit tests and doc for functions
- Integrate Travis, code quality, goreport and codecov
- A convinent way to dynamic reload the server when code changing, you can use `fresh` to run server in `app` directory
- There is a demo in pink-lady, a api service for labeling object with label, you can delete it in `apis/demo` `services/demo` `models/demo`
