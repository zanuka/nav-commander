# getaddresstxids

Returns the txids for an address(es) (requires addressindex to be enabled).

## Arguments:
```
{
  "addresses"
    [
      "address"  (string) The base58check encoded address
      ,...
    ]
  "start" (number) The start block height
  "end" (number) The end block height
}
```

## Result:
```
[
  "transactionid"  (string) The transaction id
  ,...
]
```

## Examples:
```
> navcoin-cli getaddresstxids '{"addresses": ["12c6DSiU4Rq3P4ZxziKxzrL5LmMBrzjrJX"]}'
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getaddresstxids", "params": [{"addresses": ["12c6DSiU4Rq3P4ZxziKxzrL5LmMBrzjrJX"]}] }' -H 'content-type: text/plain;' http://127.0.0.1:5555/
```