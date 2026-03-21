##### Dockerfile for C++ applications #####
## Build Stage: Compile the C++ application using the GCC image
FROM gcc:12.2.0 AS build

COPY . /opt/test
WORKDIR /opt/test

## Compile application
RUN g++ -o app app.cpp

## Run Stage: Use a lightweight Ubuntu image to run the compiled application
FROM ubuntu:bionic
WORKDIR /opt/test
COPY --from=build /opt/test ./
CMD ["./app"]