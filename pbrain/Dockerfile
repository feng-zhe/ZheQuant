FROM ubuntu:16.04
MAINTAINER Zhe Feng <henryzhefeng@gmail.com>
RUN apt-get update
RUN apt-get install -y \
    git \
    python3
COPY ZheQuant-brain-python /project/pbrain/
WORKDIR /project/pbrain/
CMD ["/bin/sh","-c","python3 pbrain.py"]
