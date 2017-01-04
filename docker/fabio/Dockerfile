FROM go:1.7.4
MAINTAINER Georg Rabenstein @raben2

RUN apk add --no-cache git
RUN go get github.com/eBay/fabio

ADD fabio.properties /fabio/fabio.properties

EXPOSE 9998 80
CMD ["/go/bin/fabio", "-cfg", "/fabio/fabio.properties"]
