FROM rust

RUN apt update && \
    apt install -y zsh

RUN chsh -s /bin/zsh

RUN useradd -m participant
USER participant

RUN cargo install cargo-atcoder

COPY ./cargo-atcoder.toml /home/participant/.config/cargo-atcoder.toml

WORKDIR /home/participant

RUN touch .zshrc