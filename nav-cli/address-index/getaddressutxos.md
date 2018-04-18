# getaddressutxos

Returns all unspent outputs for an address (requires addressindex to be enabled).

## Arguments:
    {
      "addresses"
        [
          "address"  (string) The base58check encoded address
          ,...
        ],
      "chainInfo"  (boolean) Include chain info with results
    }

## Result
    [
      {
        "address"  (string) The address base58check encoded
        "txid"  (string) The output txid
        "height"  (number) The block height
        "outputIndex"  (number) The output index
        "script"  (strin) The script hex encoded
        "satoshis"  (number) The number of satoshis of the output
      }
    ]

## Examples:
    > navcoin-cli getaddressutxos '{"addresses": ["12c6DSiU4Rq3P4ZxziKxzrL5LmMBrzjrJX"]}'
    > curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getaddressutxos", "params": [{"addresses": ["12c6DSiU4Rq3P4ZxziKxzrL5LmMBrzjrJX"]}] }' -H 'content-type: text/plain;' http://127.0.0.1:5555/