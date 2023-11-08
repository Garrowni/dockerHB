#By adding teh second from directive we are able to make it multistage
FROM golang:1.12.4 AS compiler
WORKDIR /helloworld
COPY helloworld.go .
RUN GOOS=linux go build -a -installsuffix cgo -o helloworld .

FROM alpine:3.9.3
WORKDIR /root
#copy from the previous stage!
COPY --from=compiler /helloworld/helloworld .
CMD ["./helloworld"]

