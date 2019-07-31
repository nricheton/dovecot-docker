FROM debian:stable-slim 

RUN apt-get clean && apt-get update && apt-get --no-install-recommends -y install dovecot-imapd python-pip rsyslog && apt-get clean && rm -rf /var/lib/apt/lists/* && pip install supervisor-stdout

ADD supervisord.conf /etc/supervisord.conf
ADD rsyslog.conf /etc/rsyslog.conf

EXPOSE  993 
CMD ["supervisord","-n","-c","/etc/supervisord.conf"]