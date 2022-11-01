FROM debian:stable-slim 

RUN groupadd -r -g 2000 vmail   && useradd --no-log-init -r -g vmail -u 2000 vmail

RUN apt-get clean && apt-get update && apt-get dist-upgrade && apt-get --no-install-recommends -y install git dumb-init dovecot-imapd python3-setuptools python3-pip rsyslog logrotate tzdata && apt-get clean && rm -rf /var/lib/apt/lists/* && pip install wheel && pip install supervisor git+https://github.com/coderanger/supervisor-stdout

ADD supervisord.conf /etc/supervisord.conf
ADD rsyslog.conf /etc/rsyslog.conf
ADD logrotate /etc/logrotate.d/dovecot

RUN mkdir /var/log/supervisor/

EXPOSE  993 
ENTRYPOINT ["/usr/bin/dumb-init", "--"]
CMD ["supervisord","-n","-c","/etc/supervisord.conf"]
