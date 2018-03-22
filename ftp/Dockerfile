FROM python:2.7.14-slim

ENV FTP_ROOT /ftp
ENV FTP_PORT 21

ADD . /app
WORKDIR /app

RUN pip install -r requirements.txt && mkdir -pv ${FTP_ROOT} && chmod +x /app/ftpd && ln -s /app/ftpd /usr/local/bin/ftpd

EXPOSE $FTP_PORT

CMD ["/bin/sh", "-c", "ftpd", "--port", "${FTP_PORT}"]
