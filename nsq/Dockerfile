FROM ubuntu:14.04

RUN apt-get update && apt-get install -y git mercurial curl ca-certificates && rm -rf /var/lib/apt/lists*

ENV GOLANG_VERSION 1.4.2

RUN curl -sSL https://golang.org/dl/go$GOLANG_VERSION.linux-amd64.tar.gz \
	| tar -v -C /usr/local -xz

RUN mkdir -p /go/src /go/bin && chmod -R 777 /go
ENV GOPATH /go
ENV PATH /go/bin:/usr/local/go/bin:$PATH
WORKDIR /go

RUN go get github.com/bitly/nsq/apps/nsqd
RUN go get github.com/bitly/nsq/apps/nsqadmin
RUN go get github.com/bitly/nsq/apps/nsqlookupd

RUN go get github.com/lavab/bati

ADD start.sh /

ENTRYPOINT /start.sh