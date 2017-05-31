FROM ubuntu:16.04
LABEL maintainer "henryzhefeng@gmail.com"
RUN apt-get update
RUN apt-get install -y \
        python3 \
        python3-pip \
        python3-venv \
        git
COPY ZheQuant-admin-console/ /root/admin/
WORKDIR /root/admin/
RUN ln -s /usr/bin/python3 /usr/local/bin/python && \
    ln -s /usr/bin/pip3 /usr/local/bin/pip && \
    pip install -r requirements.txt
CMD ["echo","hello"]
