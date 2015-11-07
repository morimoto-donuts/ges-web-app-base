FROM debian:8.2
COPY requirements.* /home/debian/app/
RUN cd /home/debian/app && \
  apt-get update && apt-get install -y sudo python3 wget && \
  wget https://raw.github.com/pypa/pip/master/contrib/get-pip.py && \
  python3 get-pip.py && \
  rm get-pip.py && \
  useradd -m debian && \
  echo debian:password | chpasswd && \
  gpasswd -a debian sudo && \
  pip3 install -r requirements.txt && \
  chown -R debian:debian /home/debian
USER debian
ONBUILD COPY . /home/debian/app/src/
ONBUILD WORKDIR /home/debian/app/src
ONBUILD EXPOSE 8888
ONBUILD ENTRYPOINT python3 main.py
