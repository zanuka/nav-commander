# listreceivedbyaddress ( minconf includeempty includeWatchonly)

List balances by receiving address.

## Arguments:
1. minconf       (numeric, optional, default=1) The minimum number of confirmations before payments are included.
2. includeempty  (bool, optional, default=false) Whether to include addresses that haven't received any payments.
3. includeWatchonly (bool, optional, default=false) Whether to include watchonly addresses (see 'importaddress').

## Result:
    [
      {
        "involvesWatchonly" : true,        (bool) Only returned if imported addresses were involved in transaction
        "address" : "receivingaddress",  (string) The receiving address
        "account" : "accountname",       (string) DEPRECATED. The account of the receiving address. The default account is "".
        "amount" : x.xxx,                  (numeric) The total amount in NAV received by the address
        "confirmations" : n,               (numeric) The number of confirmations of the most recent transaction included
        "label" : "label"                (string) A comment for the address/transaction, if any
      }
      ,...
    ]

## Examples:
    > navcoin-cli listreceivedbyaddress
    > navcoin-cli listreceivedbyaddress 6 true
