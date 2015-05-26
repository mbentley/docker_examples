grails example
==============

## Build using Docker
* Build WAR file using Docker:
`docker run -it --rm -v ${PWD}:/data mbentley/grails:2.4.2 war helloworld.war`

* Build:
`docker build --rm -t helloworld-grails .`

* Run:
`docker run -it --rm -p 8080:8080 -e CATALINA_OPTS="-Djava.security.egd=file:/dev/./urandom" helloworld-grails`
