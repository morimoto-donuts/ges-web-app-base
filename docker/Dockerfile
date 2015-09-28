FROM debian:8.2
COPY requirements.* /home/debian/app
WORKDIR /home/debian/app
RUN apt-get update && apt-get install -y sudo python3 python3-pip && \
  useradd -m debian && \
  echo debian:password | chpasswd && \
  gpasswd -a debian sudo && \
  pip3 install -r requirements.txt
USER debian
ONBUILD COPY . /home/debian/app/src
ONBUILD WORKDIR /home/debian/app/src
ONBUILD EXPOSE 8888
ONBUILD ENTRYPOINT python3 main.py
