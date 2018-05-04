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

    root@25f0c709343e:/# navcoin-cli help "addnode"
    addnode "node" "add|remove|onetry"

Attempts add or remove a node from the addnode list.
Or try a connection to a node once.

## Arguments:
1. "node"     (string, required) The node (see getpeerinfo for nodes)
2. "command"  (string, required) 'add' to add a node to the list, 'remove' to remove a node from the list, 'onetry' to try a connection to the node once

## Examples:
    > navcoin-cli addnode "192.168.0.6:5556" "onetry"
