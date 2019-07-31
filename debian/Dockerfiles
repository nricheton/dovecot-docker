FROM debian:stable-slim 

RUN apt-get clean && apt-get update && apt-get --no-install-recommends -y dovecot-imapd supervisor rsyslog && apt-get clean && rm -rf /var/lib/apt/lists/*

ADD supervisord.conf /etc/supervisord.conf
ADD rsyslog.conf /etc/rsyslog.conf

EXPOSE  993 
CMD ["supervisord","-n","-c","/etc/supervisord.conf"]
