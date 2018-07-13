# addanonserver "node" "add|remove"

Attempts add or remove a node from the NAVTech server list.

## Arguments:
1. "node"     (string, required) The node (see getpeerinfo for nodes)
2. "command"  (string, required) 'add' to add a node to the list, 'remove' to remove a node from the list
3. save  (boolean, optional) add or remove the given node to your config file

## Examples:
    > navcoin-cli addanonserver "192.168.0.6:3000" "add"
    > navcoin-cli addanonserver "192.168.0.6:3000" "add" true