FROM alpine:3.4
MAINTAINER Georg Rabenstein @raben2

RUN apk add --no-cache python
RUN echo 'hello world' > /index.html

EXPOSE 8080

CMD ["python", "-m", "SimpleHTTPServer", "8080"]