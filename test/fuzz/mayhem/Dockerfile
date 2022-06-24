# Build Stage
FROM ubuntu:22.04 as builder

## deps
RUN apt-get update && apt-get install -y build-essential

## Add source code to the build stage.
ADD . /src
WORKDIR /src

RUN cd test/fuzz/ && make

# Package Stage
FROM ubuntu:22.04

COPY --from=builder \
    /src/test/fuzz/lwip_fuzz \
    /src/test/fuzz/lwip_fuzz2 \
    /src/test/fuzz/lwip_fuzz3 \
    /
