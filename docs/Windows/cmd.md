# CMD

## NSLOOKUP

help command

`nslookup /?`

   C:\Users\Risman>nslookup /?
   Usage:
   nslookup [-opt ...]             # interactive mode using default server
   nslookup [-opt ...] - server    # interactive mode using 'server'
   nslookup [-opt ...] host        # just look up 'host' using default server
   nslookup [-opt ...] host server # just look up 'host' using 'server'

or

`nslookup` then hit enter, then type `help`

    C:\Users\Risman>nslookup
    DNS request timed out.
    timeout was 2 seconds.
    Default Server:  UnKnown
    Address:  192.168.43.1
    >help
    Commands:   (identifiers are shown in uppercase, [] means optional)
    NAME            - print info about the host/domain NAME using default server
    NAME1 NAME2     - as above, but use NAME2 as server
    help or ?       - print info on common commands
    set OPTION      - set an option
        all                 - print options, current server and host
        [no]debug           - print debugging information
        [no]d2              - print exhaustive debugging information
        [no]defname         - append domain name to each query
        [no]recurse         - ask for recursive answer to query
        [no]search          - use domain search list
        [no]vc              - always use a virtual circuit
        domain=NAME         - set default domain name to NAME
        srchlist=N1[/N2/.../N6] - set domain to N1 and search list to N1,N2, etc.
        root=NAME           - set root server to NAME
        retry=X             - set number of retries to X
        timeout=X           - set initial time-out interval to X seconds
        type=X              - set query type (ex. A,AAAA,A+AAAA,ANY,CNAME,MX,NS,PTR,SOA,SRV)
        querytype=X         - same as type
        class=X             - set query class (ex. IN (Internet), ANY)
        [no]msxfr           - use MS fast zone transfer
        ixfrver=X           - current version to use in IXFR transfer request
    server NAME     - set default server to NAME, using current default server
    lserver NAME    - set default server to NAME, using initial server
    root            - set current default server to the root
    ls [opt] DOMAIN [> FILE] - list addresses in DOMAIN (optional: output to FILE)
        -a          -  list canonical names and aliases
        -d          -  list all records
        -t TYPE     -  list records of the given RFC record type (ex. A,CNAME,MX,NS,PTR etc.)
    view FILE           - sort an 'ls' output file and view it with pg
    exit            - exit the program

`nslookup  [hostname]`

`nslookup [hostname] [dns-server]`

`nslookup -type=CNAME [hostname]`

`nslookup -type=MX [hostname]`

`nslookup -type=ANY [hostname]`