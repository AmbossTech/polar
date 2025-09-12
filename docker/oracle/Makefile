IMAGE_NAME := my-price-oracle
NETWORK_NAME := polar-network-2_default
ORACLE_DIR := .

.PHONY: build run stop clean

build:
	docker build --no-cache -t $(IMAGE_NAME) $(ORACLE_DIR)

run:
	docker rm -f price-oracle
	docker run -d --name price-oracle --network $(NETWORK_NAME) -p 8095:8095 $(IMAGE_NAME)

stop:
	docker rm -f price-oracle

clean: stop
