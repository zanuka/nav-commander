# addnode "node" "add|remove|onetry"

Attempts add or remove a node from the addnode list.
Or try a connection to a node once.

## Arguments:
1. "node"     (string, required) The node (see getpeerinfo for nodes)
2. "command"  (string, required) 'add' to add a node to the list, 'remove' to remove a node from the list, 'onetry' to try a connection to the node once

## Examples:
    > navcoin-cli addnode "192.168.0.6:5556" "onetry"

    root@25f0c709343e:/# navcoin-cli help "addnode"
    addnode "node" "add|remove|onetry"

Attempts add or remove a node from the addnode list.
Or try a connection to a node once.

## Arguments:
1. "node"     (string, required) The node (see getpeerinfo for nodes)
2. "command"  (string, required) 'add' to add a node to the list, 'remove' to remove a node from the list, 'onetry' to try a connection to the node once

## Examples:
    > navcoin-cli addnode "192.168.0.6:5556" "onetry"