# getrawmempool ( verbose )

Returns all transaction ids in memory pool as a json array of string transaction ids.

## Arguments:
1. verbose           (boolean, optional, default=false) true for a json object, false for array of transaction ids

## Result: (for verbose = false):
    [                     (json array of string)
      "transactionid"     (string) The transaction id
      ,...
    ]

## Result: (for verbose = true):
    {                           (json object)
      "transactionid" : {       (json object)
        "size" : n,             (numeric) transaction size in bytes
        "fee" : n,              (numeric) transaction fee in NAV
        "modifiedfee" : n,      (numeric) transaction fee with fee deltas used for mining priority
        "time" : n,             (numeric) local time transaction entered pool in seconds since 1 Jan 1970 GMT
        "height" : n,           (numeric) block height when transaction entered pool
        "startingpriority" : n, (numeric) priority when transaction entered pool
        "currentpriority" : n,  (numeric) transaction priority now
        "descendantcount" : n,  (numeric) number of in-mempool descendant transactions (including this one)
        "descendantsize" : n,   (numeric) size of in-mempool descendants (including this one)
        "descendantfees" : n,   (numeric) modified fees (see above) of in-mempool descendants (including this one)
        "ancestorcount" : n,    (numeric) number of in-mempool ancestor transactions (including this one)
        "ancestorsize" : n,     (numeric) size of in-mempool ancestors (including this one)
        "ancestorfees" : n,     (numeric) modified fees (see above) of in-mempool ancestors (including this one)
        "depends" : [           (array) unconfirmed transactions used as inputs for this transaction
            "transactionid",    (string) parent transaction id
           ... ]
      }, ...
    }

## Examples
    > navcoin-cli getrawmempool true