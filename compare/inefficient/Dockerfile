#we need golang because we need golang to be compiled!
#Compiels the program and then runs the executable
FROM golang:1.12.4
WORKDIR /helloworld
COPY helloworld.go .
#compile it into an executable
RUN GOOS=linux go build -a -installsuffix cgo -o helloworld .
#run it!
CMD ["./helloworld"]

