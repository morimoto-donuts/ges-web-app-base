FROM debian:8.2
RUN apt-get update && apt-get install -y sudo python3 python3-pip && \
  useradd -m debian && \
  echo debian:password | chpasswd && \
  gpasswd -a debian sudo
USER debian
ONBUILD COPY . /home/ubuntu/app
ONBUILD WORKDIR /home/ubuntu/app
ONBUILD USER root
ONBUILD RUN pip3 install -r requirements.txt
ONBUILD EXPOSE 8888
ONBUILD ENTRYPOINT python3 main.py
