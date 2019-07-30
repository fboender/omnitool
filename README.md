# Omnitool

A tool for lazy system administrators.

Subcommands:

## myip

    $ ./ot myip
    ip: 194.187.79.11
    hostname: electricmonk.nl
    country: Netherlands
    city: ??

## netconn

    $ ./ot netconn smtp.gmail.com 25
    hostname: gmail-smtp-msa.l.google.com
    aliasses: smtp.gmail.com
    ips: 108.177.126.109
    108.177.126.109: reversehostname: [Errno 1] Unknown host
    108.177.126.109: ping: response received
    108.177.126.109:25: socket: connecting...
    108.177.126.109:25: socket: connected (something is listening there)
    108.177.126.109:25: socket: receiving data...
    108.177.126.109:25: socket: received data:
      | 220 smtp.gmail.com ESMTP x22sm1518848eds.47 - gsmtp
    108.177.126.109:25: socket: connection closed.

## sysinfo

    OS:        ubuntu (debian) v18.04
    CPU:       8 x Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz
    Load:      0.26 0.22 0.14

    Local IPs: 10.0.1.2, 10.1.14.10, 127.0.0.1, 192.168.1.25, 192.168.3.4
    Out IP:    22.20.200.22   22-200-20-22@fakeisp.com (Amsterdam, Netherlands)

                 Total       Used      Avail    Buffers     Cached       Free     Mnt
    Mem:         7.5 G                 4.6 G      0.8 G      3.0 G      1.5 G
    Swap:        1.0 G      0.0 G      1.0 G
    Disk:      231.5 G     87.6 G    132.4 G                                      /
    Disk:        0.7 G      0.3 G      0.4 G                                      /boot

