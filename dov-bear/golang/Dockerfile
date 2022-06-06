FROM golang:alpine3.16 AS application

WORKDIR /app

ADD go.mod .
ADD go.sum .
ADD main.go .

# produces main (executable)
RUN go build -o main main.go

FROM alpine:3.16

WORKDIR /app

COPY --from=application /app/main main
ADD public public
ADD templates templates

ENV PORT=3000
EXPOSE ${PORT}

ENTRYPOINT ["./main"]