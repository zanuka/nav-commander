# gettxoutsetinfo

Returns statistics about the unspent transaction output set.
Note this call may take some time.

## Result:
    {
      "height":n,     (numeric) The current block height (index)
      "bestblock": "hex",   (string) the best block hash hex
      "transactions": n,      (numeric) The number of transactions
      "txouts": n,            (numeric) The number of output transactions
      "bytes_serialized": n,  (numeric) The serialized size
      "hash_serialized": "hash",   (string) The serialized hash
      "total_amount": x.xxx          (numeric) The total amount
    }

## Examples:
    > navcoin-cli gettxoutsetinfo