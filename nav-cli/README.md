# navcoind rpc commands

## == Addressindex ==
- navcoin-cli [getaddressbalance](address-index/getaddressbalance.md)
- navcoin-cli [getaddressdeltas](address-index/getaddressdeltas.md)
- navcoin-cli [getaddressmempool](address-index/getaddressmempool.md)
- navcoin-cli [getaddresstxids](address-index/getaddresstxids.md) '{"addresses": ["address"]}'
- navcoin-cli [getaddressutxos](address-index/getaddressutxos.md)

## == Blockchain ==
- navcoin-cli [getbestblockhash](blockchain/getbestblockhash.md)
- navcoin-cli [getblock](blockchain/getblock.md) "hash"
- navcoin-cli [getblockchaininfo](blockchain/getblockchaininfo.md)
- navcoin-cli getblockcount
- navcoin-cli getblockhash index
- navcoin-cli getblockhashes timestamp
- navcoin-cli getblockheader "hash"
- navcoin-cli getchaintips
- navcoin-cli getdifficulty
- navcoin-cli getmempoolancestors txid
- navcoin-cli getmempooldescendants txid
- navcoin-cli getmempoolentry txid
- navcoin-cli getmempoolinfo
- navcoin-cli getpaymentrequest "hash"
- navcoin-cli getproposal "hash"
- navcoin-cli getrawmempool
- navcoin-cli getspentinfo
- navcoin-cli [gettxout](blockchain/gettxout.md) "txid" n
- navcoin-cli [gettxoutproof](blockchain/gettxoutproof.md) ["txid",...]
- navcoin-cli gettxoutsetinfo
- navcoin-cli verifychain
- navcoin-cli verifytxoutproof "proof"

## == Control ==
- navcoin-cli getinfo
- navcoin-cli help
- navcoin-cli stop

## == Generating ==
- navcoin-cli generate numblocks
- navcoin-cli generatetoaddress numblocks address

## == Network ==
- navcoin-cli addanonserver "node" "add/remove"
- navcoin-cli addnode "node" "add/remove/onetry"
- navcoin-cli clearbanned
- navcoin-cli disconnectnode "node"
- navcoin-cli getaddednodeinfo dummy
- navcoin-cli getconnectioncount
- navcoin-cli getnettotals
- navcoin-cli getnetworkinfo
- navcoin-cli getpeerinfo
- navcoin-cli getstakesubsidy <hex string>
- navcoin-cli listbanned
- navcoin-cli ping

## == Rawtransactions ==
- navcoin-cli [decoderawtransaction](raw-transactions/decoderawtransaction.md) "hexstring"
- navcoin-cli decodescript
- navcoin-cli getrawtransaction "txid"

## == Wallet ==
- navcoin-cli getanondestination "navcoinaddress"
- navcoin-cli getbalance
- navcoin-cli getnewaddress
- navcoin-cli getrawchangeaddress
- navcoin-cli getreceivedbyaccount "account"
- navcoin-cli getreceivedbyaddress "navcoinaddress"
- navcoin-cli getstakereport
- navcoin-cli [gettransaction](wallet/gettransaction.md) "hash"
- navcoin-cli getunconfirmedbalance
- navcoin-cli getwalletinfo
- navcoin-cli importaddress "address"
- navcoin-cli importprivkey "navcoinprivkey"
- navcoin-cli importprunedfunds
- navcoin-cli importpubkey "pubkey"
- navcoin-cli importwallet "filename"
- navcoin-cli keypoolrefill
- navcoin-cli listaccounts
- navcoin-cli listaddressgroupings
- navcoin-cli listlockunspent
- navcoin-cli listreceivedbyaccount
- navcoin-cli listreceivedbyaddress
- navcoin-cli listsinceblock
- navcoin-cli listtransactions
- navcoin-cli listunspent

