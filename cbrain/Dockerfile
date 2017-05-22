FROM ubuntu:16.04
MAINTAINER Zhe Feng <henryzhefeng@gmail.com>
RUN apt-get update
RUN apt-get install -y \
    cmake \
    g++ \
    git \
    tar \
    xz-utils \
    wget \
    libev-dev \
    libmongoc-1.0-0 \
    pkg-config \
    libssl-dev \
    libsasl2-dev \
    python
# download dependency
WORKDIR /projects/library/
RUN git clone https://github.com/CopernicaMarketingSoftware/AMQP-CPP.git && \
    wget https://github.com/mongodb/mongo-c-driver/releases/download/1.6.2/mongo-c-driver-1.6.2.tar.gz && \
    tar xf mongo-c-driver-1.6.2.tar.gz && \ 
    rm mongo-c-driver-1.6.2.tar.gz && \
    wget https://github.com/mongodb/mongo-cxx-driver/archive/r3.1.1.tar.gz && \
    tar xf r3.1.1.tar.gz && \
    rm r3.1.1.tar.gz
# install AMQP-CPP library
WORKDIR /projects/library/AMQP-CPP/
RUN make && make install
# install mongo-c-driver
WORKDIR /projects/library/mongo-c-driver-1.6.2/
RUN ./configure --disable-automatic-init-and-cleanup && \ 
    make && \ 
    make install
## install boost library
#COPY boost_1_63_0/ /projects/library/boost_1_63_0/
#WORKDIR /projects/library/boost_1_63_0/
#RUN ./bootstrap.sh && ./b2 install 
# install mongocxx driver
WORKDIR /projects/library/mongo-cxx-driver-r3.1.1/build
RUN cmake -DCMAKE_BUILD_TYPE=Release -DBSONCXX_POLY_USE_MNMLSTC=1 -DCMAKE_INSTALL_PREFIX=/usr/local .. \
    && make \
    && make install
# build and run the cbrain
# add this env because needed when running
ENV LD_LIBRARY_PATH /usr/local/
COPY ZheQuant-brain-cpp/ /projects/ZheQuant-brain-cpp/
WORKDIR /projects/ZheQuant-brain-cpp/build/
RUN cmake .. && make
CMD ["./cbrain"]
