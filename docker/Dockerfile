FROM ubuntu:20.04
ADD . /docker

ENV container docker
ENV PATH /snap/bin:$PATH
ENV TZ=America/Los_Angeles
ENV DEBIAN_FRONTEND=noninteractive

RUN cd /docker && cp snap /usr/local/bin/snap

RUN apt-get update && apt-get install -y ca-certificates \
                                         fuse \
                                         git-all \
                                         gnupg \
                                         gnupg1 \
                                         gnupg2 \
                                         locales \
                                         locales-all \
                                         snapd \
                                         squashfuse \
                                         tree \
                                         wget

ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8

RUN systemctl enable snapd
STOPSIGNAL SIGRTMIN+3

RUN cd /docker && wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb && dpkg -i erlang-solutions_2.0_all.deb

RUN apt-get update && apt-get install -y esl-erlang \
                                         elixir 
CMD [ "/sbin/init" ]
