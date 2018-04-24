# getrawtransaction "txid" ( verbose )

NOTE: By default this function only works sometimes. This is when the tx is in the mempool
or there is an unspent output in the utxo for this transaction. To make it always work,
you need to maintain a transaction index, using the -txindex command line option.

## Return the raw transaction data.

If verbose=0, returns a string that is serialized, hex-encoded data for 'txid'.
If verbose is non-zero, returns an Object with information about 'txid'.

## Arguments:
1. "txid"      (string, required) The transaction id
2. verbose       (numeric, optional, default=0) If 0, return a string, other return a json object

## Result (if verbose is not set or set to 0):
"data"      (string) The serialized, hex-encoded data for 'txid'

## Result (if verbose > 0):
    {
      "hex" : "data",       (string) The serialized, hex-encoded data for 'txid'
      "txid" : "id",        (string) The transaction id (same as provided)
      "hash" : "id",        (string) The transaction hash (differs from txid for witness transactions)
      "size" : n,             (numeric) The serialized transaction size
      "vsize" : n,            (numeric) The virtual transaction size (differs from size for witness transactions)
      "version" : n,          (numeric) The version
      "locktime" : ttt,       (numeric) The lock time
      "vin" : [               (array of json objects)
         {
           "txid": "id",    (string) The transaction id
           "vout": n,         (numeric)
           "scriptSig": {     (json object) The script
             "asm": "asm",  (string) asm
             "hex": "hex"   (string) hex
           },
           "sequence": n      (numeric) The script sequence number
           "txinwitness": ["hex", ...] (array of string) hex-encoded witness data (if any)
         }
         ,...
      ],
      "vout" : [              (array of json objects)
         {
           "value" : x.xxx,            (numeric) The value in NAV
           "n" : n,                    (numeric) index
           "scriptPubKey" : {          (json object)
             "asm" : "asm",          (string) the asm
             "hex" : "hex",          (string) the hex
             "reqSigs" : n,            (numeric) The required sigs
             "type" : "pubkeyhash",  (string) The type, eg 'pubkeyhash'
             "addresses" : [           (json array of string)
               "navcoinaddress"        (string) navcoin address
               ,...
             ]
           }
         }
         ,...
      ],
      "blockhash" : "hash",   (string) the block hash
      "confirmations" : n,      (numeric) The confirmations
      "time" : ttt,             (numeric) The transaction time in seconds since epoch (Jan 1 1970 GMT)
      "blocktime" : ttt         (numeric) The block time in seconds since epoch (Jan 1 1970 GMT)
    }

## Examples:
> navcoin-cli getrawtransaction "mytxid"
> navcoin-cli getrawtransaction "mytxid" 1
