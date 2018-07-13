# getaddressmempool

Returns all mempool deltas for an address (requires addressindex to be enabled).

## Arguments:
    {
      "addresses"
        [
          "address"  (string) The base58check encoded address
          ,...
        ]
    }

## Result:
    [
      {
        "address"  (string) The base58check encoded address
        "txid"  (string) The related txid
        "index"  (number) The related input or output index
        "satoshis"  (number) The difference of satoshis
        "timestamp"  (number) The time the transaction entered the mempool (seconds)
        "prevtxid"  (string) The previous txid (if spending)
        "prevout"  (string) The previous transaction output index (if spending)
      }
    ]

## Examples:
    > navcoin-cli getaddressmempool '{"addresses": ["12c6DSiU4Rq3P4ZxziKxzrL5LmMBrzjrJX"]}'
