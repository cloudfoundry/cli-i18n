FROM golang:latest

RUN sed -i -e 's/httpredir.debian.org/ftp.us.debian.org/' /etc/apt/sources.list
RUN apt update

RUN apt install -y git zip

RUN go version
RUN go get -u github.com/XenoPhex/i18n4go/i18n4go

ENV PATH $GOPATH/bin:$PATH
