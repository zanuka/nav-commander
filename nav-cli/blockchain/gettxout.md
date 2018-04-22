# gettxout "txid" n ( includemempool )

Returns details about an unspent transaction output.

## Arguments:
1. "txid"       (string, required) The transaction id
2. n              (numeric, required) vout number
3. includemempool  (boolean, optional) Whether to include the mem pool

## Result:
    {
      "bestblock" : "hash",    (string) the block hash
      "confirmations" : n,       (numeric) The number of confirmations
      "value" : x.xxx,           (numeric) The transaction value in NAV
      "scriptPubKey" : {         (json object)
         "asm" : "code",       (string)
         "hex" : "hex",        (string)
         "reqSigs" : n,          (numeric) Number of required signatures
         "type" : "pubkeyhash", (string) The type, eg pubkeyhash
         "addresses" : [          (array of string) array of navcoin addresses
            "navcoinaddress"     (string) navcoin address
            ,...
         ]
      },
      "version" : n,            (numeric) The version
      "coinbase" : true|false   (boolean) Coinbase or not
    }

## Examples:

### Get unspent transactions
    > navcoin-cli listunspent

### View the details
    > navcoin-cli gettxout "txid" 1
