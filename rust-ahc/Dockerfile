FROM rust

RUN apt update && \
    apt install -y zsh

RUN chsh -s /bin/zsh

RUN useradd -m participant
USER participant

WORKDIR /home/participant

RUN touch .zshrc && \
    cargo new ahc && \
    cd ahc

COPY template/main.rs ./src/main.rs
COPY template/Cargo.toml .