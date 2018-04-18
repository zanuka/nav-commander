# getaddressbalance

Returns the balance for an address(es) (requires addressindex to be enabled).

## Arguments:
    {
      "addresses"
        [
          "address"  (string) The base58check encoded address
          ,...
        ]
    }

## Result:
    {
      "balance"  (string) The current balance in satoshis
      "received"  (string) The total number of satoshis received (including change)
    }

## Examples:
    > navcoin-cli getaddressbalance '{"addresses": ["12c6DSiU4Rq3P4ZxziKxzrL5LmMBrzjrJX"]}'
    > curl --user myusername --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getaddressbalance", "params": [{"addresses": ["12c6DSiU4Rq3P4ZxziKxzrL5LmMBrzjrJX"]}] }' -H 'content-type: text/plain;' http://127.0.0.1:5555/
    