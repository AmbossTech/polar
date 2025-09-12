# syntax=docker/dockerfile:1

# Builder stage
FROM golang:1.24-alpine AS builder
RUN apk add --no-cache git make

WORKDIR /build
RUN git clone --branch jcbrand/polar-demo https://github.com/AmbossTech/taproot-assets-oracle-demo.git .

WORKDIR /build/docs/examples
RUN make

# Final image
FROM alpine:latest
RUN apk add --no-cache ca-certificates

COPY --from=builder /build/docs/examples/basic-price-oracle/basic-price-oracle /usr/local/bin/basic-price-oracle
RUN chmod +x /usr/local/bin/basic-price-oracle

EXPOSE 8095

ENTRYPOINT ["/usr/local/bin/basic-price-oracle"]
