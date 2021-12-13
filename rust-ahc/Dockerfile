FROM rust

RUN apt update && \
    apt install -y zsh

RUN chsh -s /bin/zsh

RUN touch .zshrc && \
    cargo new ahc

WORKDIR /ahc

COPY template/main.rs ./src/main.rs
COPY template/Cargo.toml .