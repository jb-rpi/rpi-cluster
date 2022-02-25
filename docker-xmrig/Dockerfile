#Docker file for xmrig:

FROM ubuntu:latest AS build

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get -y install git build-essential cmake libuv1-dev libssl-dev libhwloc-dev
WORKDIR /root
RUN git clone https://github.com/xmrig/xmrig.git
RUN mkdir xmrig/build && cd xmrig/build && cmake .. && make -j$(nproc)

FROM ubuntu:latest
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update
RUN apt-get -y install libssl-dev libhwloc-dev
RUN useradd -ms /bin/bash monero
USER monero
WORKDIR /home/monero
COPY --from=build --chown=monero /root/xmrig/build/xmrig /home/monero


# put your XMR address
ENTRYPOINT ["./xmrig"]
CMD ["--url=pool.supportxmr.com:443", "--tls", "--user=42MSnM49WuUc1UNFbnm45Y5U4Q6kxkbx953qMkdoPnkC5BN4QUFz9qHgAfqPgwK1zkJNtHayvR1
YMfN4GZgB9tbo6GnDaTB", "--pass=Docker", "-k", "--coin=monero"]
