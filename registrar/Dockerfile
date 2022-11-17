FROM golang:1.19.3-alpine

ENV APPPATH ./registrar

##RUN apt-get update -y && apt-get upgrade -y
WORKDIR $APPPATH

#RUN echo "Installing golang:1.19.3" && \
#    apt-get install wget -y && \
#    wget https://go.dev/dl/go1.19.3.linux-amd64.tar.gz &&\
#    tar -C /usr/local -xzf go1.19.3.linux-amd64.tar.gz &&\
#    export PATH=$PATH:/usr/local/go/bin >> ~/.bashrc &&\
#    source ~/.bashrc && \
#    go version

# Download necessary Go modules
COPY go.mod $APPPATH
COPY go.sum $APPPATH
COPY . .

#RUN go test -v ./tests/

RUN go build -o ./usr/bin/registrar ./cmd/registrar/

EXPOSE 8080

# set entrypoint
ENTRYPOINT [ "./usr/bin/registrar" ]