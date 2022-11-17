FROM ubuntu:latest

ENV PATH /registrar

RUN apt update -y

RUN echo "Installing golang:1.19.3" && \
    wget https://go.dev/dl/go1.19.3.linux-amd64.tar.gz &&\
    tar -C /usr/local -xzf go1.19.3.linux-amd64.tar.gz &&\
    export PATH=$PATH:/usr/local/go/bin &&\
    go version

WORKDIR $PATH

# Download necessary Go modules
COPY go.mod $PATH
COPY go.sum $PATH
COPY . $PATH
#RUN go test -v ./tests/

RUN go build -o ./usr/bin/registrar $PATH/cmd/registrar/

EXPOSE 8080

# set entrypoint
ENTRYPOINT [ "./usr/bin/registrar" ]