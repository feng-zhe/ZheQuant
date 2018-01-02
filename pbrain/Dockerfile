FROM ubuntu:16.04
MAINTAINER Zhe Feng <henryzhefeng@gmail.com>
ENV LC_ALL=C.UTF-8
ENV LANG=C.UTF-8
RUN apt-get update --fix-missing
RUN apt-get install -y python3 python3-pip git vim
COPY ZheQuant-brain-python /project/pbrain/
WORKDIR /project/pbrain/
RUN ln -s /usr/bin/python3 /usr/bin/python && \
    ln -s /usr/bin/pip3 /usr/bin/pip && \
    pip install pipenv && \
    pipenv install --dev
CMD ["pipenv", "run", "python", "main.py"]
