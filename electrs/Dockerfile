FROM rust:1.44.1-slim-buster

RUN apt-get update
RUN apt-get install -y clang cmake
RUN apt-get install -y libsnappy-dev git protobuf-compiler
RUN apt-get install -y m4

USER root
WORKDIR /root/src

# RUN git clone --depth 1 https://github.com/chaintope/electrs-tapyrus.git -b v0.2.0 /root/src
RUN git clone --depth 1 https://github.com/chaintope/electrs-tapyrus.git /root/src

RUN rustup update nightly
RUN rustup update stable

RUN cd /root/src \
  && cargo build --release \
  && cargo install --path .

# Electrum RPC
EXPOSE 50001

# Prometheus monitoring
EXPOSE 4224

STOPSIGNAL SIGINT
