##### Dockerfile for Golang applications #####
## Build Stage: Compile the Golang application using the Golang image
FROM golang:1.17-alpine as build-env

ENV APP_NAME sample-dockerize-app
ENV CMD_PATH main.go

COPY . $GOPATH/src/$APP_NAME
WORKDIR $GOPATH/src/$APP_NAME

## Build application
RUN CGO_ENABLED=0 go build -v -o /$APP_NAME $GOPATH/src/$APP_NAME/$CMD_PATH

## Run Stage: Use a lightweight Alpine image to run the compiled application
FROM alpine:3.14

ENV APP_NAME sample-dockerize-app
COPY --from=build-env /$APP_NAME .

EXPOSE 8081

CMD ./$APP_NAME