# Omnitool

A tool for lazy system administrators.

Subcommands:

## myip

Shows information about your current outgoing IP by connecting to
https://ifconfig.co/.

    $ ./ot myip
    ip: 194.187.79.11
    hostname: electricmonk.nl
    country: Netherlands
    city: ??

## netconn

Tests a network connection to a port, including reserve DNS, hostname, ping
and socket connection test.

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

Show basic system information.

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

## sslinfo

Show info about SSL / TLS certificates, etc.

    $ ./ot sslinfo *
    STAR_example_com.crt
      Certificate (PEM format)
      part 1
        Subject:      CN = *.example.com
        Issuer:       C = GB, ST = Greater Manchester, L = Salford, O = Sectigo Limited, CN = Sectigo RSA Domain Validation Secure Server CA
        Not After:    Jun 19 23:59:59 2021 GMT
        Modulus Hash: AAAFAKE846BD8204E72F680363558BC2
    STAR_example_com-intermediates.crt
      Certificate (PEM format)
      part 1
        Subject:      C = GB, ST = Greater Manchester, L = Salford, O = Sectigo Limited, CN = Sectigo RSA Domain Validation Secure Server CA
        Issuer:       C = US, ST = New Jersey, L = Jersey City, O = The USERTRUST Network, CN = USERTrust RSA Certification Authority
        Not After:    Dec 31 23:59:59 2030 GMT
        Modulus Hash: BBBFAKE23743BF8239EA08FDB6CD526C
      Certificate (PEM format)
      part 2
        Subject:      C = US, ST = New Jersey, L = Jersey City, O = The USERTRUST Network, CN = USERTrust RSA Certification Authority
        Issuer:       C = US, ST = New Jersey, L = Jersey City, O = The USERTRUST Network, CN = USERTrust RSA Certification Authority
        Not After:    Jan 18 23:59:59 2038 GMT
        Modulus Hash: CCCFAKE9920FB972EAC043DF7B85B03B
        Is Root:      Yes
    STAR_example_com.nopass.key
      Rsa private key (PEM format)
      part 1
    Unknown format

## diag

Diagnose some common Linux problems.

    $ ./ot diag
    Checking local network: Pinging default gateway 192.168.1.1: Ok
    Checking internet access: Pinging 8.8.8.8: Ok
    Checking DNS resolving: Resolving www.example.org: Ok

## json

Do stuff with json such as pretty-printing, flattening, etc.

    usage: ot json [-h] [-i INDENT] [-l] [-f] [INPUT]

    Pretty-print, flatten and other json stuff

    positional arguments:
      INPUT                 File to read from. If ommitted, read from stdin

    optional arguments:
      -h, --help            show this help message and exit
      -i INDENT, --indent INDENT
                            Indent level. 0 will output a single line
      -l, --lines           Treat input as json lines
      -f, --flatten         Flatten output

Example:

    $ cat ~/test.json
    {"people":[{"name":"John","age":24},{"name":"Pete","age":45}]}

    $ ./ot json -i 2 < ~/test.json
    {
      "people": [
        {
          "name": "John",
          "age": 24
        },
        {
          "name": "Pete",
          "age": 45
        }
      ]
    }

    $ ./ot json -f < ~/test.json
    people[0].name = John
    people[0].age = 24
    people[1].name = Pete
    people[1].age = 45

