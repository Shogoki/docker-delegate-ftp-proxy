FROM debian:latest
#EXPOSE 22
EXPOSE 21
RUN apt-get update \
&& apt-get -y dist-upgrade \
&& apt-get -y install wget
RUN  wget -O /usr/bin/delegate http://delegate.hpcc.jp/anonftp/DeleGate/bin-latest9/linux2.6-dg9_9_13
RUN chmod 755 /usr/bin/delegate
RUN echo '#!/bin/bash' > /srv/delegate-entry
RUN echo '/usr/bin/delegate -P21 SERVER=ftp  ADMIN="mail@admin.local" RELIABLE="*" LOGDIR=/var/log SRCIF="*:0:ftp-data" PERMIT="ftp:*:*"  SRCIF="*:30000-30009:ftp-data-pasv" -r -f' >> /srv/delegate-entry
RUN chmod 755 /srv/delegate-entry
#RUN chmod 755 /entrypoint
ENTRYPOINT ["/srv/delegate-entry"]
