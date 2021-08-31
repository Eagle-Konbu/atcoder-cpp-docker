FROM rust

RUN apt update && \
    apt install -y zsh

RUN chsh -s /bin/zsh

RUN useradd -m competitor
USER competitor

RUN cargo install cargo-atcoder

COPY ./cargo-atcoder.toml /home/competitor/.config/cargo-atcoder.toml

WORKDIR /home/competitor

RUN touch .zshrc