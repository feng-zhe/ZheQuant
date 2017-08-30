FROM ubuntu:16.04
MAINTAINER Zhe Feng <henryzhefeng@gmail.com>
RUN apt-get update
RUN apt-get install -y \
    git \
    python3
COPY ZheQuant-brain-python /project/pbrain/
WORKDIR /project/pbrain/
RUN pip3 install -r requirements.txt
CMD ["/bin/sh","-c","python3 main.py"]
