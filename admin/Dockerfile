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
RUN python3 -m venv venv
# source is not a valid command in Dockerfile RUN
RUN /bin/bash -c "source venv/bin/activate && pip install -r requirements.txt && ./main.py -g test_data"
CMD ["echo","hello"]
