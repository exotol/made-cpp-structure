FROM ubuntu:20.04

RUN mkdir cpp && cd /cpp
WORKDIR cpp

RUN  apt-get update \
  && apt-get install -y wget \
  && wget https://releases.linaro.org/components/toolchain/binaries/7.3-2018.05/arm-linux-gnueabi/gcc-linaro-7.3.1-2018.05-x86_64_arm-linux-gnueabi.tar.xz \
  && wget https://releases.linaro.org/components/toolchain/binaries/7.3-2018.05/arm-linux-gnueabi/sysroot-glibc-linaro-2.25-2018.05-arm-linux-gnueabi.tar.xz

RUN  apt-get update \
  && apt-get install -y software-properties-common \
  && apt-get install xz-utils \
  && apt-get install nano \
  && apt-get install -y qemu-user \
  && rm -rf /var/lib/apt/lists/*

RUN tar -xf gcc-linaro-7.3.1-2018.05-x86_64_arm-linux-gnueabi.tar.xz \
   && tar -xf sysroot-glibc-linaro-2.25-2018.05-arm-linux-gnueabi.tar.xz \
   && mv gcc-linaro-7.3.1-2018.05-x86_64_arm-linux-gnueabi gcc-linaro \
	&& mv sysroot-glibc-linaro-2.25-2018.05-arm-linux-gnueabi sysroot \
	&& echo 'PATH="$PATH:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin"' >> ~/.bashrc \
	&& echo 'PATH="$PATH:/cpp/gcc-linaro/bin"' >> ~/.bashrc \
	&& echo 'export LINARO_SYSROOT=/cpp/sysroot' >> ~/.bashrc \
	&& . ~/.bashrc

RUN mkdir code

COPY ./code/ /cpp/code/
RUN ls -la /cpp/code/*