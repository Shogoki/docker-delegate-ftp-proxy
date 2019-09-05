FROM alpine:latest

EXPOSE 21

RUN apk update \
&& apk upgrade \
&& apk add wget && \
wget -O /usr/bin/delegate http://delegate.hpcc.jp/anonftp/DeleGate/bin-latest9/linux2.6-dg9_9_13 && \ 
chmod 755 /usr/bin/delegate
#RUN apk add libgcc sigblock
##glibc
RUN apk --no-cache add ca-certificates && \
wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub && \
wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.30-r0/glibc-2.30-r0.apk && \
 apk add glibc-2.30-r0.apk 

RUN wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.30-r0/glibc-dev-2.30-r0.apk && \
apk add glibc-dev-2.30-r0.apk
RUN apk add \ 
libnsl \ 
libbsd \ 
libbsd-dev libnsl-dev && ln -s /usr/lib/libnsl.so.2 /usr/lib/libnsl.so.1

RUN wget -O /usr/lib/libstdc++.so.6.0.2 https://raw.githubusercontent.com/orctom/alpine-glibc-packages/master/usr/lib/libstdc++.so.6.0.21 && \
ln -s /usr/lib/libstdc++.so.6.0.21 /usr/lib/libstdc++.so.6.new &&  mv /usr/lib/libstdc++.so.6.new /usr/lib/libstdc++.so.6


ADD entrypoint /srv/delegate-entry
RUN chmod 755 /srv/delegate-entry
#RUN chmod 755 /entrypoint
CMD ["/srv/delegate-entry"]
