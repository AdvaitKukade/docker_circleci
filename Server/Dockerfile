#Server-side docker file.

FROM alpine
WORKDIR /serverdata

COPY ./createfile.sh /serverdata
COPY ./ServerFile.sh /home
RUN apk add git && apk add tar && apk add gzip 
RUN apk add openrc
RUN apk add openssh
RUN apk add sshpass
RUN rc-status
RUN touch /run/openrc/softlevel

RUN sh ./createfile.sh
ENTRYPOINT ["/bin/sh","/home/ServerFile.sh"]

RUN adduser --disabled-password --gecos "" server
RUN echo server:123456 | chpasswd
