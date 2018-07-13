# getnetworkinfo
Returns an object containing various state info regarding P2P networking.

## Result:
    {
      "version": xxxxx,                      (numeric) the server version
      "subversion": "/Satoshi:x.x.x/",     (string) the server subversion string
      "protocolversion": xxxxx,              (numeric) the protocol version
      "localservices": "xxxxxxxxxxxxxxxx", (string) the services we offer to the network
      "localrelay": true|false,              (bool) true if transaction relay is requested from peers
      "timeoffset": xxxxx,                   (numeric) the time offset
      "connections": xxxxx,                  (numeric) the number of connections
      "networks": [                          (array) information per network
      {
        "name": "xxx",                     (string) network (ipv4, ipv6 or onion)
        "limited": true|false,               (boolean) is the network limited using -onlynet?
        "reachable": true|false,             (boolean) is the network reachable?
        "proxy": "host:port"               (string) the proxy that is used for this network, or empty if none
      }
      ,...
      ],
      "relayfee": x.xxxxxxxx,                (numeric) minimum relay fee for non-free transactions in NAV/kB
      "localaddresses": [                    (array) list of local addresses
      {
        "address": "xxxx",                 (string) network address
        "port": xxx,                         (numeric) network port
        "score": xxx                         (numeric) relative score
      }
      ,...
      ]
      "warnings": "..."                    (string) any network warnings (such as alert messages)
    }

## Examples:
    > navcoin-cli getnetworkinfo