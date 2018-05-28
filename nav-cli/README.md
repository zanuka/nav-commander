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
- navcoin-cli [getblockcount](blockchain/getblockcount.md)
- navcoin-cli [getblockhash](blockchain/getblockhash.md) index
- navcoin-cli [getblockhashes](blockchain/getblockhashes.md) timestamp
- navcoin-cli [getblockheader](blockchain/getblockheader.md) "hash"
- navcoin-cli [getchaintips](blockchain/getchaintips.md)
- navcoin-cli [getdifficulty](blockchain/getdifficulty.md)
- navcoin-cli [getmempoolancestors](blockchain/getmempoolancestors.md) txid
- navcoin-cli [getmempooldescendants](blockchain/getmempooldescendants.md) txid
- navcoin-cli [getmempoolentry](blockchain/getmempoolentry.md) txid
- navcoin-cli [getmempoolinfo](blockchain/getmempoolinfo.md)
- navcoin-cli [getpaymentrequest](blockchain/getpaymentrequest.md) "hash"
- navcoin-cli [getproposal](blockchain/getproposal.md) "hash"
- navcoin-cli [getrawmempool](blockchain/getrawmempool.md) ( verbose )
- navcoin-cli [getspentinfo](blockchain/getspentinfo.md)
- navcoin-cli [gettxout](blockchain/gettxout.md) "txid" n
- navcoin-cli [gettxoutproof](blockchain/gettxoutproof.md) ["txid",...]
- navcoin-cli [gettxoutsetinfo](blockchain/gettxoutsetinfo.md)
- navcoin-cli [verifychain](blockchain/verifychain.md)
- navcoin-cli [verifytxoutproof](blockchain/verifytxoutproof.md) "proof"

## == Control ==
- navcoin-cli [getinfo](control/getinfo.md)
- navcoin-cli [help](control/help.md)
- navcoin-cli [stop](control/stop.md)

## == Generating ==
- navcoin-cli [generate](generating/generate.md) numblocks
- navcoin-cli [generatetoaddress](generating/generatetoaddress.md) numblocks address

## == Network ==
- navcoin-cli [addanonserver](network/addanonserver.md) "node" "add/remove"
- navcoin-cli [addnode](network/addnode.md) "node" "add/remove/onetry"
- navcoin-cli [clearbanned](network/clearbanned.md)
- navcoin-cli [disconnectnode](network/disconnectnode.md) "node"
- navcoin-cli [getaddednodeinfo](network/getaddednodeinfo.md) dummy
- navcoin-cli [getconnectioncount](network/getconnectioncount.md)
- navcoin-cli getnettotals
- navcoin-cli getnetworkinfo
- navcoin-cli getpeerinfo
- navcoin-cli getstakesubsidy <hex string>
- navcoin-cli listbanned
- navcoin-cli ping

## == Rawtransactions ==
- navcoin-cli [decoderawtransaction](raw-transactions/decoderawtransaction.md) "hexstring"
- navcoin-cli [decodescript](raw-transactions/decodescript.md)
- navcoin-cli [getrawtransaction](raw-transactions/getrawtransaction.md) "txid"

## == Wallet ==
- navcoin-cli [getanondestination](wallet/getanondestination.md) "navcoinaddress"
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

