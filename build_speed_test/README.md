# May 5, 2017 tests
# uname -a
Linux graphtest 4.4.0-38-generic #57~14.04.1-Ubuntu SMP Tue Sep 6 17:20:43 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

### aufs
```
root@graphtest ~/d/build_speed_test:master:0:0# docker info
Containers: 0
 Running: 0
 Paused: 0
 Stopped: 0
Images: 0
Server Version: 17.03.1-ce
Storage Driver: aufs
 Root Dir: /var/lib/docker/aufs
 Backing Filesystem: extfs
 Dirs: 0
 Dirperm1 Supported: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins:
 Volume: local
 Network: bridge host macvlan null overlay
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: 4ab9917febca54791c5f071a9d1f404867857fcc
runc version: 54296cf40ad8143b62dbcaa1d90e520a2136ddfe
init version: 949e6fa
Security Options:
 apparmor
Kernel Version: 4.4.0-38-generic
Operating System: Ubuntu 14.04.5 LTS
OSType: linux
Architecture: x86_64
CPUs: 1
Total Memory: 1.445 GiB
Name: graphtest
ID: TI6K:CLO4:W6LU:XVBQ:YVKV:T3KL:JKT5:MNAK:ZGDO:SB6A:73QH:BUGE
Docker Root Dir: /var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
Registry: https://index.docker.io/v1/
WARNING: No swap limit support
Experimental: false
Insecure Registries:
 127.0.0.0/8
Live Restore Enabled: false
```
```
root@ubuntu ~/d/build_speed_test:master:0:0# time docker build --no-cache -f Dockerfile.scratch -t test .
Sending build context to Docker daemon 6.144 kB
Step 1/6 : FROM scratch
 --->
Step 2/6 : ADD . /
 ---> 8bb98afc80ce
Removing intermediate container 284dcba4ba9b
Step 3/6 : WORKDIR /
 ---> d7e6201bae4c
Removing intermediate container 691993e6c133
Step 4/6 : USER 1
 ---> Running in 2963543023f6
 ---> edd272edb45f
Removing intermediate container 2963543023f6
Step 5/6 : ENTRYPOINT /bin/bash
 ---> Running in 44e66a98c8c4
 ---> b69c9ae27754
Removing intermediate container 44e66a98c8c4
Step 6/6 : CMD -l
 ---> Running in 5a16c1395378
 ---> 1e772f4e1ff7
Removing intermediate container 5a16c1395378
Successfully built 1e772f4e1ff7

real    0m0.302s
user    0m0.016s
sys     0m0.000s
```
```
root@ubuntu ~/d/build_speed_test:master:0:0# time docker build --no-cache -f Dockerfile.jessie -t test .
Sending build context to Docker daemon 6.144 kB
Step 1/6 : FROM debian:jessie
 ---> 054abe38b1e6
Step 2/6 : ADD . /
 ---> 0a3c326e0436
Removing intermediate container 2edeb49f76c3
Step 3/6 : WORKDIR /
 ---> 89c9f805ea79
Removing intermediate container fe7150b1b824
Step 4/6 : USER 1
 ---> Running in 2d05ed2c5d79
 ---> 1ef4666326d9
Removing intermediate container 2d05ed2c5d79
Step 5/6 : ENTRYPOINT /bin/bash
 ---> Running in a59dbb01607f
 ---> 31425587dd7c
Removing intermediate container a59dbb01607f
Step 6/6 : CMD -l
 ---> Running in 0ab0e7466919
 ---> 59927ecd8d1c
Removing intermediate container 0ab0e7466919
Successfully built 59927ecd8d1c

real    0m0.300s
user    0m0.012s
sys     0m0.004s
```
```
root@ubuntu ~/d/build_speed_test:master:0:0# time docker build --no-cache -f Dockerfile.gcc -t test .
Sending build context to Docker daemon 6.144 kB
Step 1/6 : FROM gcc:4.9
 ---> 8015972a9896
Step 2/6 : ADD . /
 ---> 7672b7f942a5
Removing intermediate container 77ac8c29a95d
Step 3/6 : WORKDIR /
 ---> 959b7e052090
Removing intermediate container 54db9d1214e9
Step 4/6 : USER 1
 ---> Running in cfa915e12ebe
 ---> f25b9b8096b9
Removing intermediate container cfa915e12ebe
Step 5/6 : ENTRYPOINT /bin/bash
 ---> Running in fe3c24c121b1
 ---> 850ee671a43d
Removing intermediate container fe3c24c121b1
Step 6/6 : CMD -l
 ---> Running in c85f7ecf5d17
 ---> 196e24101f8a
Removing intermediate container c85f7ecf5d17
Successfully built 196e24101f8a

real    0m0.340s
user    0m0.004s
sys     0m0.004s
```


### devicemapper direct-lvm
```
root@graphtest ~# docker info
Containers: 0
 Running: 0
 Paused: 0
 Stopped: 0
Images: 0
Server Version: 17.03.1-ce
Storage Driver: devicemapper                                                                                           Pool Name: docker-thinpool-tpool
 Pool Blocksize: 524.3 kB
 Base Device Size: 10.74 GB
 Backing Filesystem: ext4
 Data file:                                                                                                            Metadata file:
 Data Space Used: 312 MB
 Data Space Total: 12.23 GB
 Data Space Available: 11.92 GB
 Metadata Space Used: 65.54 kB
 Metadata Space Total: 125.8 MB
 Metadata Space Available: 125.8 MB
 Thin Pool Minimum Free Space: 1.223 GB
 Udev Sync Supported: true
 Deferred Removal Enabled: false
 Deferred Deletion Enabled: false
 Deferred Deleted Device Count: 0
 Library Version: 1.02.77 (2012-10-15)
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins:
 Volume: local
 Network: bridge host macvlan null overlay
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: 4ab9917febca54791c5f071a9d1f404867857fcc
runc version: 54296cf40ad8143b62dbcaa1d90e520a2136ddfe
init version: 949e6fa
Security Options:
 apparmor
Kernel Version: 4.4.0-38-generic
Operating System: Ubuntu 14.04.5 LTS
OSType: linux
Architecture: x86_64
CPUs: 1
Total Memory: 1.445 GiB
Name: graphtest
ID: TI6K:CLO4:W6LU:XVBQ:YVKV:T3KL:JKT5:MNAK:ZGDO:SB6A:73QH:BUGE
Docker Root Dir: /var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
Registry: https://index.docker.io/v1/
WARNING: No swap limit support
Experimental: false
Insecure Registries:
 127.0.0.0/8
Live Restore Enabled: false
```
```
root@graphtest ~/d/build_speed_test:master:0:0# time docker build --no-cache -f Dockerfile.scratch -t test .
Sending build context to Docker daemon 6.144 kB
Step 1/6 : FROM scratch
 --->
Step 2/6 : ADD . /
 ---> b71f8c9a0f07
Removing intermediate container 7ac28c6960c3
Step 3/6 : WORKDIR /
 ---> e503c4070bb7
Removing intermediate container c08a4608b67a
Step 4/6 : USER 1
 ---> Running in 5982ab530f37
 ---> 2f9026898812
Removing intermediate container 5982ab530f37
Step 5/6 : ENTRYPOINT /bin/bash
 ---> Running in 42adfe3cbd49
 ---> 05bea4431c4e
Removing intermediate container 42adfe3cbd49
Step 6/6 : CMD -l
 ---> Running in 8c31cb3fff97
 ---> f13815c784ab
Removing intermediate container 8c31cb3fff97
Successfully built f13815c784ab

real    0m4.841s
user    0m0.016s
sys     0m0.000s
```
```
root@graphtest ~/d/build_speed_test:master:0:0# time docker build --no-cache -f Dockerfile.jessie -t test .
Sending build context to Docker daemon 6.144 kB
Step 1/6 : FROM debian:jessie
 ---> 054abe38b1e6
Step 2/6 : ADD . /
 ---> 3257831c6b1e
Removing intermediate container e8d01f273a33
Step 3/6 : WORKDIR /
 ---> e9f0c03c168b
Removing intermediate container 89d048a70c4b
Step 4/6 : USER 1
 ---> Running in c1688ccef8b0
 ---> a93b32bdefa7
Removing intermediate container c1688ccef8b0
Step 5/6 : ENTRYPOINT /bin/bash
 ---> Running in 40d80b7e6092
 ---> aedb0446e07b
Removing intermediate container 40d80b7e6092
Step 6/6 : CMD -l
 ---> Running in 3870a4fa6aad
 ---> 9e5e3655177f
Removing intermediate container 3870a4fa6aad
Successfully built 9e5e3655177f

real    0m4.835s
user    0m0.008s
sys     0m0.000s
```
```
root@graphtest ~/d/build_speed_test:master:0:0# time docker build --no-cache -f Dockerfile.gcc -t test .
Sending build context to Docker daemon 6.144 kB
Step 1/6 : FROM gcc:4.9
 ---> 8015972a9896
Step 2/6 : ADD . /
 ---> 507301925cd6
Removing intermediate container 53729baaecb7
Step 3/6 : WORKDIR /
 ---> 82eae9b9d0fb
Removing intermediate container beae69f0c333
Step 4/6 : USER 1
 ---> Running in 0618c69dfef1
 ---> 18daa4daf628
Removing intermediate container 0618c69dfef1
Step 5/6 : ENTRYPOINT /bin/bash
 ---> Running in d2c49a1402ba
 ---> 16a517e2df0f
Removing intermediate container d2c49a1402ba
Step 6/6 : CMD -l
 ---> Running in c49f7289eca7
 ---> 179e54269ef8
Removing intermediate container c49f7289eca7
Successfully built 179e54269ef8

real    0m38.762s
user    0m0.008s
sys     0m0.004s
```


### overlay
```
root@graphtest ~/d/build_speed_test:master:0:0# docker info
Containers: 0
 Running: 0
 Paused: 0
 Stopped: 0
Images: 0
Server Version: 17.03.1-ce
Storage Driver: overlay
 Backing Filesystem: extfs
 Supports d_type: true
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins:
 Volume: local
 Network: bridge host macvlan null overlay
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: 4ab9917febca54791c5f071a9d1f404867857fcc
runc version: 54296cf40ad8143b62dbcaa1d90e520a2136ddfe
init version: 949e6fa
Security Options:
 apparmor
Kernel Version: 4.4.0-38-generic
Operating System: Ubuntu 14.04.5 LTS
OSType: linux
Architecture: x86_64
CPUs: 1
Total Memory: 1.445 GiB
Name: graphtest
ID: TI6K:CLO4:W6LU:XVBQ:YVKV:T3KL:JKT5:MNAK:ZGDO:SB6A:73QH:BUGE
Docker Root Dir: /var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
Registry: https://index.docker.io/v1/
WARNING: No swap limit support
Experimental: false
Insecure Registries:
 127.0.0.0/8
Live Restore Enabled: false
```
```
root@graphtest ~/d/build_speed_test:master:0:0# time docker build --no-cache -f Dockerfile.scratch -t test .
Sending build context to Docker daemon 6.144 kB
Step 1/6 : FROM scratch
 --->
Step 2/6 : ADD . /
 ---> 977151e6f85e
Removing intermediate container 22c909ab8400
Step 3/6 : WORKDIR /
 ---> a857c5f87ada
Removing intermediate container 7491f20dea82
Step 4/6 : USER 1
 ---> Running in b805283960cc
 ---> 7b59568ad3d3
Removing intermediate container b805283960cc
Step 5/6 : ENTRYPOINT /bin/bash
 ---> Running in 3bed9fdd010f
 ---> 20c11fd10918
Removing intermediate container 3bed9fdd010f
Step 6/6 : CMD -l
 ---> Running in 30fea762699a
 ---> f3e36beb0813
Removing intermediate container 30fea762699a
Successfully built f3e36beb0813

real    0m4.359s
user    0m0.012s
sys     0m0.000s
```
```
root@graphtest ~/d/build_speed_test:master:0:0# time docker build --no-cache -f Dockerfile.jessie -t test .
Sending build context to Docker daemon 6.144 kB
Step 1/6 : FROM debian:jessie
 ---> 054abe38b1e6
Step 2/6 : ADD . /
 ---> 3f8034362958
Removing intermediate container 88b4b0616826
Step 3/6 : WORKDIR /
 ---> 4438303317d9
Removing intermediate container 0e34977f740d
Step 4/6 : USER 1
 ---> Running in e7677e46911a
 ---> 11b88dfb3c42
Removing intermediate container e7677e46911a
Step 5/6 : ENTRYPOINT /bin/bash
 ---> Running in fd2bc4a7119b
 ---> b7de4a90516d
Removing intermediate container fd2bc4a7119b
Step 6/6 : CMD -l
 ---> Running in c89c3bb906a5
 ---> 8a72921399c4
Removing intermediate container c89c3bb906a5
Successfully built 8a72921399c4

real    0m4.475s
user    0m0.004s
sys     0m0.008s
```
```
root@graphtest ~/d/build_speed_test:master:0:0# time docker build --no-cache -f Dockerfile.gcc -t test .
Sending build context to Docker daemon 6.144 kB
Step 1/6 : FROM gcc:4.9
 ---> 8015972a9896
Step 2/6 : ADD . /
 ---> b8a8e763bc53
Removing intermediate container d16888fb37c0
Step 3/6 : WORKDIR /
 ---> b3d14a0519d0
Removing intermediate container 0c48e5e66774
Step 4/6 : USER 1
 ---> Running in 585cf29dde10
 ---> 6f0f9d65bc71
Removing intermediate container 585cf29dde10
Step 5/6 : ENTRYPOINT /bin/bash
 ---> Running in 258127a7abbe
 ---> 98f1948dd724
Removing intermediate container 258127a7abbe
Step 6/6 : CMD -l
 ---> Running in 98687beb6d5e
 ---> 1ac408dd8918
Removing intermediate container 98687beb6d5e
Successfully built 1ac408dd8918

real    0m37.011s
user    0m0.004s
sys     0m0.008s
```

### overlay2
```
root@graphtest ~/d/build_speed_test:master:0:0# docker info
Containers: 0
 Running: 0
 Paused: 0
 Stopped: 0
Images: 0
Server Version: 17.03.1-ce
Storage Driver: overlay2
 Backing Filesystem: extfs
 Supports d_type: true
 Native Overlay Diff: false
Logging Driver: json-file
Cgroup Driver: cgroupfs
Plugins:
 Volume: local
 Network: bridge host macvlan null overlay
Swarm: inactive
Runtimes: runc
Default Runtime: runc
Init Binary: docker-init
containerd version: 4ab9917febca54791c5f071a9d1f404867857fcc
runc version: 54296cf40ad8143b62dbcaa1d90e520a2136ddfe
init version: 949e6fa
Security Options:
 apparmor
Kernel Version: 4.4.0-38-generic
Operating System: Ubuntu 14.04.5 LTS
OSType: linux
Architecture: x86_64
CPUs: 1
Total Memory: 1.445 GiB
Name: graphtest
ID: TI6K:CLO4:W6LU:XVBQ:YVKV:T3KL:JKT5:MNAK:ZGDO:SB6A:73QH:BUGE
Docker Root Dir: /var/lib/docker
Debug Mode (client): false
Debug Mode (server): false
Registry: https://index.docker.io/v1/
WARNING: No swap limit support
Experimental: false
Insecure Registries:
 127.0.0.0/8
Live Restore Enabled: false
```
```
root@graphtest ~/d/build_speed_test:master:0:0# time docker build --no-cache -f Dockerfile.scratch -t test .
Sending build context to Docker daemon 6.144 kB
Step 1/6 : FROM scratch
 --->
Step 2/6 : ADD . /
 ---> a4335bd0fa12
Removing intermediate container d812c5b37dbc
Step 3/6 : WORKDIR /
 ---> 1377815c11f6
Removing intermediate container 4c74eb0cedcf
Step 4/6 : USER 1
 ---> Running in 06f1ca3de71a
 ---> a952ca94f084
Removing intermediate container 06f1ca3de71a
Step 5/6 : ENTRYPOINT /bin/bash
 ---> Running in 76ced23cf8aa
 ---> 0754f1891eaa
Removing intermediate container 76ced23cf8aa
Step 6/6 : CMD -l
 ---> Running in d57f30176097
 ---> fbd0c1fe1e4d
Removing intermediate container d57f30176097
Successfully built fbd0c1fe1e4d

real    0m4.402s
user    0m0.012s
sys     0m0.000s
```
```
root@graphtest ~/d/build_speed_test:master:0:0# time docker build --no-cache -f Dockerfile.jessie -t test .
Sending build context to Docker daemon 6.144 kB
Step 1/6 : FROM debian:jessie
 ---> 054abe38b1e6
Step 2/6 : ADD . /
 ---> 4ea93e5246cf
Removing intermediate container 63904dccf6e1
Step 3/6 : WORKDIR /
 ---> 2d2ad2166888
Removing intermediate container 74b636337e84
Step 4/6 : USER 1
 ---> Running in 7ce4a22ba97a
 ---> 2270c4b8b579
Removing intermediate container 7ce4a22ba97a
Step 5/6 : ENTRYPOINT /bin/bash
 ---> Running in 726225fe6ad3
 ---> 3bb1440ebfa2
Removing intermediate container 726225fe6ad3
Step 6/6 : CMD -l
 ---> Running in 8436b8d28f7d
 ---> 5b1d18ab94da
Removing intermediate container 8436b8d28f7d
Successfully built 5b1d18ab94da

real    0m4.969s
user    0m0.008s
sys     0m0.000s
```
```
root@graphtest ~/d/build_speed_test:master:0:0# time docker build --no-cache -f Dockerfile.gcc -t test .
Sending build context to Docker daemon 6.144 kB
Step 1/6 : FROM gcc:4.9
 ---> 8015972a9896
Step 2/6 : ADD . /
 ---> 5f9088503947
Removing intermediate container 0edd3c4ff082
Step 3/6 : WORKDIR /
 ---> ff5668f595b0
Removing intermediate container 9660601ca27b
Step 4/6 : USER 1
 ---> Running in 55c7f442f381
 ---> 7920d255e0e5
Removing intermediate container 55c7f442f381
Step 5/6 : ENTRYPOINT /bin/bash
 ---> Running in 926ef7fcbfc5
 ---> d3fddb6bd5b8
Removing intermediate container 926ef7fcbfc5
Step 6/6 : CMD -l
 ---> Running in 09ae23a07e17
 ---> b5f13be31f10
Removing intermediate container 09ae23a07e17
Successfully built b5f13be31f10

real    0m20.606s
user    0m0.012s
sys     0m0.000s
```

# June 1, 2015 tests
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
