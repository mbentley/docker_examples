golang example
==============

## Build using Docker, optimize with minimal image
* Compile using Docker:
`docker run -it --rm -v ${PWD}:/hello -w /hello golang:1.3-cross go build -v`

* Build:
`docker build --rm -f Dockerfile -t helloworld-go .`

* Run:
`docker run -it --rm helloworld-go`
