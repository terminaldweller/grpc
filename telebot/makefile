DST_DIR?=./protobuf/v1
SRC_DIR?=./protobuf/v1
PROTOBUF_SRC_LIST:=$(shell find ./protobuf -name '*.proto' )
ARTIFACT_LIST:=$(patsubst %.proto, %.pb.go, $(shell find ./protobuf -name '*.proto'))

DEFAULT: default

default: $(ARTIFACT_LIST)

$(SRC_DIR)/%.pb.go:$(SRC_DIR)/%.proto
	protoc --proto_path=$(SRC_DIR) --go_out=$(DST_DIR) --go_opt=paths=source_relative $<
	if [ -d go.mod ];then : else;go mod init github.com/terminaldweller/grpc/telebot/protobuf/v1;fi
	go mod tidy

clean:
	- rm $(ARTIFACT_LIST)
