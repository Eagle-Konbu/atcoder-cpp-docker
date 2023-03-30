# AtCoder Library(ACL)を使えるようにする
FROM alpine:latest as ACL_Downloader

RUN apk upgrade && \
    apk add --no-cache git

RUN git clone https://github.com/atcoder/ac-library.git /lib/ac-library

# boostを使えるようにする
FROM debian:buster-slim as Boost_Downloader

RUN apt update && \
    apt install -y build-essential wget zip && \
    wget https://boostorg.jfrog.io/artifactory/main/release/1.81.0/source/boost_1_81_0.tar.gz -O boost_1_81_0.tar.gz && \
    tar xf boost_1_81_0.tar.gz && \
    cd boost_1_81_0 && \
    ./bootstrap.sh --with-toolset=gcc --without-libraries=mpi,graph_parallel && \
    ./b2 -j3 toolset=gcc variant=release link=static runtime-link=static cxxflags="-std=c++20" stage && \
    sudo ./b2 -j3 toolset=gcc variant=release link=static runtime-link=static cxxflags="-std=c++20" --prefix=/opt/boost/gcc install

FROM debian:buster-slim

RUN apt update && \
    apt install -y g++-12 libgmp3-dev libeigen3-dev=3.4.0-2ubuntu2 zsh xclip && \
    chsh -s /bin/zsh

COPY --from=ACL_Downloader /lib/ac-library /opt/ac-library
COPY --from=Boost_Downloader /opt/boost /opt/boost

WORKDIR /home/procon/

RUN echo "alias g++='g++ -std=gnu++20 -Wall -Wextra -O2'" >> ~/.zshrc && \
    echo "alias pbcopy='xclip -selection clipboard'" >> ~/.zshrc && \
    mkdir template

COPY template.cpp ./template/
COPY template.cpp ./main.cpp
