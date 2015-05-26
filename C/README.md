C example
=========

## Build and Run in Docker
* Build: 
`docker build --rm -t helloworld .`

* Run:
`docker run -it --rm helloworld`

## Build using Docker, optimize with minimal image
* Compile using Docker:
`docker run -it --rm -v ${PWD}:/build -w /build gcc:4.9 gcc -static -o hello hello.c`

* Build Smaller Image:
`docker build --rm -f Dockerfile.smaller -t helloworld-smaller .`

* Run:
`docker run -it --rm helloworld-smaller`
