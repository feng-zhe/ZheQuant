FROM ubuntu:16.04
MAINTAINER Zhe Feng <henryzhefeng@gmail.com>
RUN apt-get update --fix-missing
RUN apt-get install -y python3 python3-pip git
COPY ZheQuant-brain-python /project/pbrain/
WORKDIR /project/pbrain/
RUN ln -s /usr/bin/python3 /usr/bin/python && \
    ln -s /usr/bin/pip3 /usr/bin/pip && \
    pip install -r requirements.txt
CMD ["/bin/sh","-c","python3 main.py"]
