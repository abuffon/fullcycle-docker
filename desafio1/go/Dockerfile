FROM golang AS builder

WORKDIR /go/src
COPY hello.go .
RUN go build hello.go

FROM scratch

COPY --from=builder /go/src/hello ./
ENTRYPOINT ["./hello"]
