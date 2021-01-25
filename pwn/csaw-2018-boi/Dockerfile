# sudo docker build -t boi .
# sudo docker run -d -p 1000:1000 -rm -it boi

FROM ubuntu:20.04

RUN apt-get update
RUN apt-get install xinetd -y 
RUN apt-get install net-tools -y

RUN useradd -d /home/ctf/ -m -p ctf -s /bin/bash ctf
RUN echo "ctf:ctf" |chpasswd

WORKDIR /home/ctf

COPY boi .
COPY flag .
COPY ./boi.xinetd /etc/xinetd.d/boi
COPY ./start.sh /start.sh

RUN chmod +x /start.sh



RUN chown -R root:root /home/ctf

USER ctf

CMD ["/start.sh"]
EXPOSE 1024 
