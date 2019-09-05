FROM debian:latest

EXPOSE 21

RUN apt-get update \
&& apt-get -y dist-upgrade \
&& apt-get -y install wget && \ 
wget -O /usr/bin/delegate http://delegate.hpcc.jp/anonftp/DeleGate/bin-latest9/linux2.6-dg9_9_13 && \ 
chmod 755 /usr/bin/delegate

ADD entrypoint /srv/delegate-entry
RUN chmod 755 /srv/delegate-entry
#RUN chmod 755 /entrypoint
ENTRYPOINT ["/srv/delegate-entry"]
