FROM buildpack-deps:stretch

RUN sed -i 's/archive.ubuntu.com/mirror.aarnet.edu.au\/pub\/ubuntu\/archive/g' /etc/apt/sources.list && \
    echo 'deb http://kr.archive.ubuntu.com/ubuntu/ focal main restricted' >> /etc/apt/sources.list && \
    echo 'deb http://kr.archive.ubuntu.com/ubuntu/ focal-updates main restricted' >> /etc/apt/sources.list && \
    echo 'deb http://kr.archive.ubuntu.com/ubuntu/ focal universe' >> /etc/apt/sources.list && \
    echo 'deb http://kr.archive.ubuntu.com/ubuntu/ focal-updates universe' >> /etc/apt/sources.list && \
    echo 'deb http://kr.archive.ubuntu.com/ubuntu/ focal multiverse' >> /etc/apt/sources.list && \
    echo 'deb http://kr.archive.ubuntu.com/ubuntu/ focal-updates multiverse' >> /etc/apt/sources.list && \
    echo 'deb http://kr.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse' >> /etc/apt/sources.list && \
    echo 'deb http://security.ubuntu.com/ubuntu focal-security main restricted' >> /etc/apt/sources.list && \
    echo 'deb http://security.ubuntu.com/ubuntu focal-security universe' >> /etc/apt/sources.list

RUN rm -rf /var/lib/apt/lists/*
RUN apt-get update --allow-unauthenticated -y && apt-get install --allow-unauthenticated -y \
    libjansson-dev  libnice-dev         libssl-dev \
    gstreamer1.0-tools libsofia-sip-ua-dev libglib2.0-dev \
    libopus-dev     libogg-dev          libini-config-dev \
    libcollection-dev libconfig-dev     pkg-config \
    gengetopt       libtool             autopoint \
    automake        build-essential     subversion \
    git             cmake               unzip \
    zip             texinfo             lsof \ 
    wget            vim                 sudo \ 
    rsync           cron                mysql-client \ 
    openssh-server  supervisor          locate \ 
    mplayer         valgrind            certbot \ 
    python-certbot-apache dnsutils      tcpdump \
    net-tools       libcurl4-gnutls-dev libgnutls28-dev

RUN cd /tmp && \
    git clone https://github.com/Karlson2k/libmicrohttpd.git && \
    cd /tmp/libmicrohttpd && \
    git checkout tags/v0.9.59 && \
	 ./bootstrap && \
	 ./configure && \
	make && make install

RUN cd /tmp && \
    wget https://github.com/cisco/libsrtp/archive/v2.2.0.tar.gz -O libsrtp-v2.2.0.tar.gz && \
    tar xfv libsrtp-v2.2.0.tar.gz && \
    cd libsrtp-2.2.0 && \   
    ./configure --prefix=/usr --enable-openssl && \
	make shared_library && sudo make install 

RUN cd /tmp && \
    git clone https://github.com/sctplab/usrsctp.git && \
    cd usrsctp && \
    mkdir build && \
    cd build && \
    cmake .. && \
    make && make install 

CMD ["/bin/bash"]
