FROM nsqio/nsq

RUN apt-get update && apt-get install -y git curl ca-certificates && rm -rf /var/lib/apt/lists*

ENV GOLANG_VERSION 1.4.2

RUN curl -sSL https://golang.org/dl/go$GOLANG_VERSION.linux-amd64.tar.gz \
	| tar -v -C /usr/local -xz

RUN mkdir -p /go/src /go/bin && chmod -R 777 /go
ENV GOPATH /go
ENV PATH /go/bin:/usr/local/go/bin:$PATH
WORKDIR /go

RUN go get github.com/lavab/bati

CMD "bati -config /etc/bati.conf &; "
