# AtCoder Library(ACL)を使えるようにする
FROM alpine:latest as ACL_Downloader

RUN apk upgrade && \
    apk add --no-cache git

RUN git clone https://github.com/atcoder/ac-library.git /lib/ac-library

FROM debian:buster-slim

RUN apt update && \
    apt install -y g++ zsh xclip && \
    apt clean && \
    rm -rf /var/lib/apt/lists/* && \
    chsh -s /bin/zsh

COPY --from=ACL_Downloader /lib/ac-library /lib/ac-library
ENV CPLUS_INCLUDE_PATH /lib/ac-library

WORKDIR /home/procon/

RUN echo "alias g++='g++ -std=gnu++17 -Wall -Wextra -O2'" >> ~/.zshrc && \
    echo "alias pbcopy='xclip -selection clipboard'" >> ~/.zshrc && \
    mkdir template

COPY template.cpp ./template/
COPY template.cpp ./main.cpp