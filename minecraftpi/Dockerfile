#FROM ubuntu:latest 
FROM ryankurte/docker-rpi-emu

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/London

RUN apt-get update -y \ 
    && apt-get install wget tar -y \ 
    && mkdir /minecraft \ 
    && cd /minecraft \
    && wget https://www.minecraft.net/content/dam/minecraft/edition-pi/minecraft-pi-0.1.1.tar.gz \
    && apt-get install default-jdk git -y \
    && tar -zxvf minecraft-pi-0.1.1.tar.gz \
    && cd mcpi

#ENTRYPOINT ["/minecraft"]
CMD tail -f /dev/null
