FROM debian:buster-slim

RUN apt update && \
    apt install -y git zsh g++ python3 python3-pip nodejs npm && \
    pip3 install numpy networkx online-judge-tools && \
    npm i -g atcoder-cli && \
    git clone https://github.com/atcoder/ac-library.git /lib/ac-library

ENV CPLUS_INCLUDE_PATH /lib/ac-library

RUN acc config default-template cpp
COPY template.json /root/.config/atcoder-cli-nodejs/cpp/
COPY main.cpp /root/.config/atcoder-cli-nodejs/cpp/

RUN echo "PROMPT='%~ [%*] %#'" >> /root/.zshrc

WORKDIR /home/procon/