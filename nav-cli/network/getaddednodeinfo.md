# getaddednodeinfo dummy ( "node" )

Returns information about the given added node, or all added nodes
(note that onetry addnodes are not listed here)

## Arguments:
1. dummy      (boolean, required) Kept for historical purposes but ignored
2. "node"   (string, optional) If provided, return information about this specific node, otherwise all nodes are returned.

## Result:
    [
      {
        "addednode" : "192.168.0.201",   (string) The node ip address or name (as provided to addnode)
        "connected" : true|false,          (boolean) If connected
        "addresses" : [                    (list of objects) Only when connected = true
           {
             "address" : "192.168.0.201:5556",  (string) The navcoin server IP and port we're connected to
             "connected" : "outbound"           (string) connection, inbound or outbound
           }
         ]
      }
      ,...
    ]

## Examples:
    > navcoin-cli getaddednodeinfo true
    > navcoin-cli getaddednodeinfo true "192.168.0.201"
