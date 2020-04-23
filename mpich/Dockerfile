FROM ubuntu:16.04

ARG MPICH_VERSION="3.3.2"
 
RUN apt-get update && apt-get install -y --fix-missing build-essential wget tzdata dialog apt-utils && \
    ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo "Asia/Shanghai" > /etc/timezone && \
    rm -f /etc/localtime && \
    rm -rf  /usr/share/zoneinfo/UTC && \
    dpkg-reconfigure -f noninteractive tzdata && \
    mkdir -p /tmp/mpich-src && \
    cd /tmp/mpich-src && \
    wget http://www.mpich.org/static/downloads/${MPICH_VERSION}/mpich-${MPICH_VERSION}.tar.gz && \ 
    tar xfz mpich-${MPICH_VERSION}.tar.gz && \ 
    cd mpich-${MPICH_VERSION} && \ 
    ./configure --disable-fortran -prefix=/mpich && \
    make && \
    make install && \
    cd /tmp && rm -rf mpich-src
ENV LANG zh_CN.utf8
ENV PATH=/mpich/bin:$PATH
ENV CGO_LDFLAGS='-L/mpich/lib/ -lmpich'
ENV CPLUS_INCLUDE_PATH=/mpich/include:/mpich/lib
ENV C_INCLUDE_PATH=/mpich/include:/mpich/lib
ENV LD_LIBRARY_PATH=/mpich/include:/mpich/lib