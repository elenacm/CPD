FROM debian:stretch as builder
ENV BINUTILS_VER 2.31
ENV GCC_VER 4.5.3
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get -y update && \
apt-get install -y \
wget \
tar \
xz-utils \
gzip && \
rm -rf /var/lib/apt/lists/*
RUN wget https://www.ohwr.org/project/wr-cores/uploads/2776ce0ba43503d1486ae205b48fb450/lm32_host_64bit.tar.xz && \
tar xvf lm32_host_64bit.tar.xz && \
mkdir -p opt/lm32 && \
cp -r lm32-gcc-${GCC_VER}/* /opt/lm32
FROM debian:stretch
RUN apt-get -y update && \
 apt-get install -y \
 make \
 cmake && \
 rm -rf /var/lib/apt/lists/*
COPY --from=builder /opt/lm32 /opt/lm32
ENV PATH "/opt/lm32/bin:$PATH"