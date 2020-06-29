FROM ubuntu:18.04

RUN apt-get update && apt-get install wget jq curl git  -y

COPY ./ /opt/application

# Install EOS Contract Development Toolkit
RUN wget -O eosio.deb https://github.com/EOSIO/eos/releases/download/v2.0.6/eosio_2.0.6-1-ubuntu-18.04_amd64.deb; \
    apt install -y ./eosio.deb; \
    rm ./eosio.deb

RUN wget -O eosio.cdt.deb https://github.com/EOSIO/eosio.cdt/releases/download/v1.7.0/eosio.cdt_1.7.0-1-ubuntu-18.04_amd64.deb; \
    apt install -y ./eosio.cdt.deb; \
    rm ./eosio.cdt.deb

VOLUME /opt/application
WORKDIR /opt/application

## Add the wait script to the image
ADD ./utils/wait /wait
RUN chmod +x /wait

# used by start.sh
ENV DATA_DIR /root/data-dir
ENV CONFIG_DIR /opt/application/config
