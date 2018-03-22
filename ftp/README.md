Running with `docker`
---

    $ docker run --rm pyftpd ftpd --help

    usage: ftpd [options]

    Simple FTP server

    optional arguments:
      -v, --version         show program's version number and exit
      --help                Show help message
      -h HOST, --host HOST  Hostname to run FTP server
      -p PORT, --port PORT  Port to run FTP server
      -P PASSIVE_PORTS, --passive-ports PASSIVE_PORTS
                            A range of passive ports. Format: start-end. Example:
                            3000-3009. Passing this option will for FTP server to
                            work in passive mode
      -u USER, --user USER  Format: username:password:[permissions],...
      -a, --anonymous       Allow anonymous user
      -n NAT, --nat NAT     NAT address

### All options

    $ docker run --rm -p 2121:21 -p 3000-3009:3000-3009 pyftpd ftpd -u user1:password_for_user1 user2:password_for_user2 -P 3000-3009 -n 172.0.0.1 -a -h 0.0.0.0

Running with `docker-compose`
---

    version: '3'

    services:
      pyftpd:
        image: pyftpd
        command: ftpd -u user1:secret1 -u user2:secret2 -p 21 -P 3000-3009
        ports:
          - "3000-3009:3000-3009"
          - "2121:21"

If you need to expose volumes to host machine:

    volumes:
        - ./ftp_data:/ftp
