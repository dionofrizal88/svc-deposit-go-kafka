# svc-deposit-go-kafka

## Kafka

**Running docker:**
```
$ docker-compose up -d
```
**Create deposits topic:**
```
$ docker-compose exec broker kafka-topics --create --bootstrap-server \ localhost:9092 --replication-factor 1 --partitions 1 --topic deposits
```
**List topic:**
```
$ docker-compose exec broker kafka-topics --list --bootstrap-server localhost:9092
```


**Initialize the Go project:**
Initialize the Go project using the following command
```
$ go mod init deposit
```

**Adding the modules required for the project:**
**Get all module in go.mod:**
```
$ go get google.golang.org/protobuf/cmd/protoc-gen-go@v1.28
$ go get google.golang.org/grpc/cmd/protoc-gen-go-grpc@latest
$ eksekusi export PATH="$PATH:$(go env GOPATH)/bin"
$ go get github.com/lovoo/goka
```
**Generate protobuf:**
```
$ protoc --go_out=paths=source_relative:. --go-grpc_out=paths=source_relative:. model/deposit.proto 
```

**Run the backend app**
```
$ go run main.go
```
