golang example
==============

## Build using Docker, optimize with minimal image
* Compile using Docker:
`docker run -it --rm -v ${PWD}:/hello -w /hello -e CGO_ENABLED=0 golang:1.3-cross go build -a -tags 'netgo' -ldflags '-w -linkmode external -extldflags -static' -v`

* Build:
`docker build --rm -t helloworld-go .`

* Run:
`docker run -it --rm -p 9999:9999 helloworld-go`
