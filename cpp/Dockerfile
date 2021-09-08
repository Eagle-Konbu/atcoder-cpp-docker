# AtCoder Library(ACL)を使えるようにする
FROM alpine:latest as ACL_Downloader

RUN apk upgrade && \
    apk add --no-cache git

RUN git clone https://github.com/atcoder/ac-library.git /lib/ac-library

FROM alpine:latest

RUN apk add --no-cache gcc libc-dev g++ zsh

COPY --from=ACL_Downloader /lib/ac-library /lib/ac-library
ENV CPLUS_INCLUDE_PATH /lib/ac-library

RUN echo "alias g++='g++ -std=gnu++17 -Wall -Wextra -O2'" > ~/.zshrc && \
    mkdir template

COPY template.cpp ./template/
COPY template.cpp ./a.cpp
