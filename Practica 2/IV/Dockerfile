FROM alpine:3.8

COPY ./calculopi.c calculopi.c

RUN apk update && apk add g++

RUN g++ calculopi.c -o calculopi