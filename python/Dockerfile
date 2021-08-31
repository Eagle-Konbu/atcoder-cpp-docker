FROM python

RUN apt update && \
    apt install -y zsh

RUN pip install networkx numpy

RUN chsh -s /bin/zsh

WORKDIR /home/procon