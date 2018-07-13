# decodescript "hex"

Decode a hex-encoded script.

## Arguments:
1. "hex"     (string) the hex encoded script

## Result:
    {
      "asm":"asm",   (string) Script public key
      "hex":"hex",   (string) hex encoded public key
      "type":"type", (string) The output type
      "reqSigs": n,    (numeric) The required signatures
      "addresses": [   (json array of string)
         "address"     (string) navcoin address
         ,...
      ],
      "p2sh","address" (string) script address
    }

## Examples:
    > navcoin-cli decodescript "hexstring"