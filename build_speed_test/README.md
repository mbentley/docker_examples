## `aufs` graph driver
  - scratch: `time docker build --no-cache -f Dockerfile.scratch -t test .`
  ```
real	0m0.481s
user	0m0.020s
sys 	0m0.000s
  ```

  - debian:jessie: `time docker build --no-cache -f Dockerfile.jessie -t test .`
  ```
real	0m0.577s
user	0m0.016s
sys 	0m0.000s
  ```

  - gcc:4.9: `time docker build --no-cache -f Dockerfile.gcc -t test .`
  ```
real	0m0.547s
user	0m0.012s
sys 	0m0.008s
  ```


## `devicemapper` graph driver
  - scratch: `time docker build --no-cache -f Dockerfile.scratch -t test .`
  ```
real	0m5.149s
user	0m0.012s
sys 	0m0.008s
  ```

  - debian:jessie: `time docker build --no-cache -f Dockerfile.jessie -t test .`
  ```
real	0m8.329s
user	0m0.020s
sys 	0m0.000s
  ```

  - gcc:4.9: `time docker build --no-cache -f Dockerfile.gcc -t test .`
  ```
real	0m51.638s
user	0m0.012s
sys 	0m0.008s
  ```


## `overlay` graph driver
  - scratch: `time docker build --no-cache -f Dockerfile.scratch -t test .`
  ```
real	0m0.650s
user	0m0.016s
sys 	0m0.004s
  ```

  - debian:jessie: `time docker build --no-cache -f Dockerfile.jessie -t test .`
  ```
real	0m3.793s
user	0m0.020s
sys 	0m0.000s
  ```

  - gcc:4.9: `time docker build --no-cache -f Dockerfile.gcc -t test .`
  ```
real	0m48.403s
user	0m0.016s
sys 	0m0.004s
  ```
