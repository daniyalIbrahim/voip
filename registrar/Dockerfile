FROM ubuntu:latest

ENV PATH /registrar
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