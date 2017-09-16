FROM ubuntu:16.04
MAINTAINER Zhe Feng <henryzhefeng@gmail.com>
# make two run because apt-get update is time consuming
RUN apt-get update
RUN apt-get install -y wget xz-utils
# download nodejs binary
WORKDIR /
RUN wget https://nodejs.org/dist/v6.10.3/node-v6.10.3-linux-x64.tar.xz && \
    tar xf node-v6.10.3-linux-x64.tar.xz && \
    cp -r /node-v6.10.3-linux-x64/* / && \
    rm node-v6.10.3-linux-x64.tar.xz && \
    rm -rf node-v6.10.3-linux-x64
RUN npm install -g watchify browserify pm2 gulp
COPY ZheQuant-webserver-backend/ /web/
WORKDIR /web/
RUN npm install && \
    npm run build
CMD ["/bin/bash", "-c", "pm2 start bin/www --name fin --watch && pm2 logs"]
