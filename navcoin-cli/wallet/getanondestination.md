# getanondestination "navcoinaddress"

Get the the encrypted anon destination and address to send to.

## Arguments:
1. "navcoinaddress"  (string, required) The navcoin address to send to.

## Result:
"anondestination"  (string) The encrypted information to attach to the transaction.
"anonaddress"  (string) The nav coin address to send the anon transaction to.

## Examples:
    > navcoin-cli getanondestination "1M72Sfpbz1BPpXFHz9m3CdqATR44Jvaydd"