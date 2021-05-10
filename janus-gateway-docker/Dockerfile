FROM sea5727/janus-gateway-base:latest

# with custom http config from my janus-gateway git repository
RUN cd /tmp && \
    git clone https://github.com/sea5727/janus-gateway.git

RUN cd /tmp/janus-gateway && \
    egrep -i "j-din.iptime.org" * -r && \
    sh autogen.sh &&  \
    rm -rf /opt/janus && \
    ./configure \
    --prefix=/opt/janus \ 
    # --enable-post-processing \
    # --enable-boringssl \
    --enable-data-channels \
    --disable-rabbitmq \
    --disable-mqtt \
    --disable-unix-sockets \
#     --enable-dtls-settimeout \
    --enable-plugin-echotest \
    --enable-plugin-recordplay \
    --enable-plugin-sip \
    --enable-plugin-videocall \
    --enable-plugin-voicemail \
    --enable-plugin-textroom \
    --enable-rest \
    --enable-turn-rest-api \
    --enable-plugin-audiobridge \
    --enable-plugin-nosip \
    --enable-all-handlers && \
    make && \ 
    make install && \ 
    make configs && \ 
    ldconfig && \
    egrep -i "j-din.iptime.org" * -r

# COPY cert.crt cert.key /tmp/
# RUN mkdir -p /opt/janus/certs && \
#     mv /tmp/cert.crt /opt/janus/certs/cert.crt && \
#     mv /tmp/cert.key /opt/janus/certs/cert.key 

# EXPOSE 20000-40000/udp
CMD ["/opt/janus/bin/janus"]
# CMD ["/opt/janus/bin/janus", "--stun-server=stun.l.google.com:19302"]