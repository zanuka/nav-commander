# navcoin-cli commands

## == Addressindex ==
    getaddressbalance
    getaddressdeltas
    getaddressmempool
    getaddresstxids
    getaddressutxos

## == Blockchain ==
    getbestblockhash
    getblock "hash" ( verbose )
    getblockchaininfo
    getblockcount

    getblockhash index
    getblockhashes timestamp
    getblockheader "hash" ( verbose )
    getchaintips
    getdifficulty
    getmempoolancestors txid (verbose)
    getmempooldescendants txid (verbose)
    getmempoolentry txid
    getmempoolinfo
    getpaymentrequest "hash"
    getproposal "hash"
    getrawmempool ( verbose )
    getspentinfo
    gettxout "txid" n ( includemempool )
    gettxoutproof ["txid",...] ( blockhash )
    gettxoutsetinfo
    verifychain ( checklevel numblocks )
    verifytxoutproof "proof"

## == Control ==
    getinfo
    help ( "command" )
    stop

## == Generating ==
    generate numblocks ( maxtries )
    generatetoaddress numblocks address (maxtries)

## == Mining ==
    getblocktemplate ( "jsonrequestobject" )
    getmininginfo
    getnetworkhashps ( blocks height )
    prioritisetransaction <txid> <priority delta> <fee delta>
    submitblock "hexdata" ( "jsonparametersobject" )

## == Network ==
    addanonserver "node" "add|remove"
    addnode "node" "add|remove|onetry"
    clearbanned
    disconnectnode "node"
    getaddednodeinfo dummy ( "node" )
    getconnectioncount
    getnettotals
    getnetworkinfo
    getpeerinfo
    getstakesubsidy <hex string>
    getstakinginfo
    listbanned
    ping
    setban "ip(/netmask)" "add|remove" (bantime) (absolute)

## == Rawtransactions ==
    createrawtransaction [{"txid":"id","vout":n},...] {"address":amount,"data":"hex",...} [anon-destination] ( locktime )
    decoderawtransaction "hexstring"
    decodescript "hex"
    fundrawtransaction "hexstring" ( options )
    getrawtransaction "txid" ( verbose )
    sendrawtransaction "hexstring" ( allowhighfees )
    signrawtransaction "hexstring" ( [{"txid":"id","vout":n,"scriptPubKey":"hex","redeemScript":"hex"},...] ["privatekey1",...] sighashtype )

## == Util ==
    createmultisig nrequired ["key",...]
    createwitnessaddress "script"
    estimatefee nblocks
    estimatepriority nblocks
    estimatesmartfee nblocks
    estimatesmartpriority nblocks
    signmessagewithprivkey "privkey" "message"
    validateaddress "navcoinaddress"
    verifymessage "navcoinaddress" "signature" "message"

## == Wallet ==
    abandontransaction "txid"
    addmultisigaddress nrequired ["key",...] ( "account" )
    addwitnessaddress "address"
    anonsend "navcoinaddress" amount ( "comment" "comment-to" )
    backupwallet "destination"
    createpaymentrequest hash amount id
    createproposal address amount deadline
    donatefund amount ( subtractfeefromamount )
    dumpmasterprivkey
    dumpprivkey "navcoinaddress"
    dumpwallet "filename"
    encryptwallet "passphrase"
    getaccount "navcoinaddress"
    getaccountaddress "account"
    getaddressesbyaccount "account"
    getanondestination "navcoinaddress"
    getbalance ( "account" minconf includeWatchonly )
    getnewaddress ( "account" )
    getrawchangeaddress
    getreceivedbyaccount "account" ( minconf )
    getreceivedbyaddress "navcoinaddress" ( minconf )
    getstakereport
    gettransaction "txid" ( includeWatchonly )
    getunconfirmedbalance
    getwalletinfo
    importaddress "address" ( "label" rescan p2sh )
    importprivkey "navcoinprivkey" ( "label" rescan )
    importprunedfunds
    importpubkey "pubkey" ( "label" rescan )
    importwallet "filename"
    keypoolrefill ( newsize )
    listaccounts ( minconf includeWatchonly)
    listaddressgroupings
    listlockunspent
    listreceivedbyaccount ( minconf includeempty includeWatchonly)
    listreceivedbyaddress ( minconf includeempty includeWatchonly)
    listsinceblock ( "blockhash" target-confirmations includeWatchonly)
    listtransactions ( "account" count from includeWatchonly)
    listunspent ( minconf maxconf  ["address",...] )
    lockunspent unlock ([{"txid":"txid","vout":n},...])
    move "fromaccount" "toaccount" amount ( minconf "comment" )
    paymentrequestvote "request_hash" "yes|no|remove"
    proposalvote "proposal_hash" "yes|no|remove"
    removeprunedfunds "txid"
    sendfrom "fromaccount" "tonavcoinaddress" amount ( minconf "comment" "comment-to" )
    sendmany "fromaccount" {"address":amount,...} ( minconf "comment" ["address",...] )
    sendtoaddress "navcoinaddress" amount ( "comment" "comment-to" "anon-destination" subtractfeefromamount )
    setaccount "navcoinaddress" "account"
    settxfee amount
    signmessage "navcoinaddress" "message"
    stakervote vote