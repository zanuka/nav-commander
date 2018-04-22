# getaddressdeltas

Returns all changes for an address (requires addressindex to be enabled).

## Arguments:
    {
      "addresses"
        [
          "address"  (string) The base58check encoded address
          ,...
        ]
      "start" (number) The start block height
      "end" (number) The end block height
      "chainInfo" (boolean) Include chain info in results, only applies if start and end specified
    }

## Result:
    [
      {
        "satoshis"  (number) The difference of satoshis
        "txid"  (string) The related txid
        "index"  (number) The related input or output index
        "height"  (number) The block height
        "address"  (string) The base58check encoded address
      }
    ]

## Examples:
    > navcoin-cli getaddressdeltas '{"addresses": ["12c6DSiU4Rq3P4ZxziKxzrL5LmMBrzjrJX"]}'
