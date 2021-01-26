# sudo docker build -t tamu19_pwn1 .
# sudo docker run -d -p 1025:1025 --rm -it tamu19_pwn1

FROM ubuntu:20.04

RUN apt-get update
RUN apt-get install xinetd -y 
RUN apt-get install net-tools -y
RUN apt-get install gcc-multilib -y

RUN useradd -d /home/ctf/ -m -p ctf -s /bin/bash ctf
RUN echo "ctf:ctf" |chpasswd

WORKDIR /home/ctf

COPY pwn1 .
COPY flag.txt .
COPY ./tamu19_pwn1.xinetd /etc/xinetd.d/tamu19_pwn1
COPY ./start.sh /start.sh

RUN chmod +x /start.sh



RUN chown -R root:root /home/ctf

USER ctf

CMD ["/start.sh"]
EXPOSE 1025
