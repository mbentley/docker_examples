FROM gcc:4.9
COPY . /build
WORKDIR /build
RUN gcc -o hello hello.c
CMD ["/build/hello"]
