# getblock "hash" ( verbose )

If verbose is false, returns a string that is serialized, hex-encoded data for block 'hash'.
If verbose is true, returns an Object with information about block <hash>.

## Arguments:
1. "hash"          (string, required) The block hash
2. verbose           (boolean, optional, default=true) true for a json object, false for the hex encoded data

## Result (for verbose = true):
    {
      "hash" : "hash",     (string) the block hash (same as provided)
      "confirmations" : n,   (numeric) The number of confirmations, or -1 if the block is not on the main chain
      "size" : n,            (numeric) The block size
      "strippedsize" : n,    (numeric) The block size excluding witness data
      "weight" : n           (numeric) The block weight (BIP 141)
      "height" : n,          (numeric) The block height or index
      "version" : n,         (numeric) The block version
      "versionHex" : "00000000", (string) The block version formatted in hexadecimal
      "merkleroot" : "xxxx", (string) The merkle root
      "tx" : [               (array of string) The transaction ids
         "transactionid"     (string) The transaction id
         ,...
      ],
      "time" : ttt,          (numeric) The block time in seconds since epoch (Jan 1 1970 GMT)
      "mediantime" : ttt,    (numeric) The median block time in seconds since epoch (Jan 1 1970 GMT)
      "nonce" : n,           (numeric) The nonce
      "bits" : "1d00ffff", (string) The bits
      "difficulty" : x.xxx,  (numeric) The difficulty
      "chainwork" : "xxxx",  (string) Expected number of hashes required to produce the chain up to this block (in hex)
      "previousblockhash" : "hash",  (string) The hash of the previous block
      "nextblockhash" : "hash"       (string) The hash of the next block
    }

## Result (for verbose=false):
    "data"             (string) A string that is serialized, hex-encoded data for block 'hash'.

## Examples:
    > navcoin-cli getblock "00000000c937983704a73af28acdec37b049d214adbda81d7e2a3dd146f6ed09"
