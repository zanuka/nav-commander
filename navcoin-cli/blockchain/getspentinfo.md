# getspentinfo

Returns the txid and index where an output is spent.

## Arguments:
    {
      "txid" (string) The hex string of the txid
      "index" (number) The start block height
    }

## Result:
    {
      "txid"  (string) The transaction id
      "index"  (number) The spending input index
      ,...
    }

## Examples:
    > navcoin-cli getspentinfo '{"txid": "11a7071a43a8da2b9ac116865a6cd92c985c3f7cbde63933d253f88dffaa311a", "index": 0}'