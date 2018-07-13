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

To get transaction ids for a NAV address:

    > navcoin-cli getaddresstxids '{"addresses": ["NW7uXr4ZAeJKigMGnKbSLfCBQY59cH1T8G"]}'

If addressindex is enabled, this should return an array of transaction ids (txids):

    [
      "c6b6063a0512ed40958bff62a48168b4b30f89cb6bce22b722f8a6d00fcb9d98",
      "08f87e9de0fd9be71bc91f42d45c48bb9494df5d5df47df7354eec0adbf35731",
      "52489abff43212445d432f6042e5b9faf99b3c843a79210629b5383f52694ec5",
      "01f7b0831f174beb8a9b0990ca8bae197f6f1e4fe3d306c755d9f52da5687a9d"
    ]

To enable addressindex, edit the navcoin.conf file:

**/root/.navcoin4/navcoin.conf`**

`addressindex=1`

After enabling addressindex you'll need to reboot the instance with `docker-compose up`

Once the updated chain info downloaded, you'll be able to run `getaddresstxids` successfully.

## Authentication

If you want to execute the rpc commands, you'll need to pass credentials:

    > navcoin-cli -rpcuser=youruser -rpcpassword=yourpassword getaddresstxids '{"addresses":
    ["NW7uXr4ZAeJKigMGnKbSLfCBQY59cH1T8G"]}'

To avoid entering `-rpcuser` and `-rpcpassword` flags with each command, add them to the navcoin.conf file:

**/root/.navcoin4/navcoin.conf**

    addressindex=1
    rpcuser=youruser
    rpcpassword=yourpassword

