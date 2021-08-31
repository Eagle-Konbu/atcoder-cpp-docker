FROM python

RUN apt update && \
    apt install zsh

RUN pip install networkx numpy

RUN chsh -s /bin/zsh

WORKDIR /home/procon