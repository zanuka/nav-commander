# getinfo
Returns an object containing various state info.

## Result:
    {
      "version": xxxxx,           (numeric) the server version
      "protocolversion": xxxxx,   (numeric) the protocol version
      "walletversion": xxxxx,     (numeric) the wallet version
      "balance": xxxxxxx,         (numeric) the total navcoin balance of the wallet
      "blocks": xxxxxx,           (numeric) the current number of blocks processed in the server
      "timeoffset": xxxxx,        (numeric) the time offset
      "connections": xxxxx,       (numeric) the number of connections
      "proxy": "host:port",     (string, optional) the proxy used by the server
      "difficulty": xxxxxx,       (numeric) the current difficulty
      "testnet": true|false,      (boolean) if the server is using testnet or not
      "keypoololdest": xxxxxx,    (numeric) the timestamp (seconds since GMT epoch) of the oldest pre-generated key in the key pool
      "keypoolsize": xxxx,        (numeric) how many new keys are pre-generated
      "unlocked_until": ttt,      (numeric) the timestamp in seconds since epoch (midnight Jan 1 1970 GMT) that the wallet is unlocked for transfers, or 0 if the wallet is locked
      "paytxfee": x.xxxx,         (numeric) the transaction fee set in NAV/kB
      "relayfee": x.xxxx,         (numeric) minimum relay fee for non-free transactions in NAV/kB
      "errors": "..."           (string) any error messages
    }

## Examples:
    > navcoin-cli getinfo