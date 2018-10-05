# docker run -it --rm -p 9987:9987/udp -p 10011:10011/tcp -p 30033:30033/tcp <name/id>
FROM debian
EXPOSE 9987/udp
EXPOSE 10011/tcp
EXPOSE 30033/tcp
ENV TS3SERVER_LICENSE accept
RUN apt-get update && apt-get install -y bzip2 wget
RUN adduser teamspeak --disabled-password --gecos ""
RUN su teamspeak
WORKDIR /home/teamspeak
RUN wget http://dl.4players.de/ts/releases/3.4.0/teamspeak3-server_linux_amd64-3.4.0.tar.bz2
RUN tar xvfj teamspeak3-server_linux_amd64-3.4.0.tar.bz2
WORKDIR /home/teamspeak/teamspeak3-server_linux_amd64
CMD ["sh", "ts3server_minimal_runscript.sh", "createinfile=1"]
