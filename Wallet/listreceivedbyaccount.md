## listreceivedbyaccount

**listreceivedbyaccount ( minconf includeempty includeWatchonly )**

DEPRECATED

The `listreceivedbyaccount` method lists balances by account.

### Arguments

| Name             | Type                               | Description                                                  |
| ---------------- | ---------------------------------- | ------------------------------------------------------------ |
| minconf          | (numeric, optional, default=1)     | the minimum number of confirmations before payments are included |
| includeempty     | (boolean, optional, default=false) | whether to include accounts that haven't received any payments |
| includeWatchonly | (bool, optional, default=false)    | whether to include watchonly addresses (see 'importaddress') |

### Response

| Name                | Type      | Description                                                  |
| ------------------- | --------- | ------------------------------------------------------------ |
| "involvesWatchonly" | (bool)    | only returned if the imported addresses were involved in the transaction |
| "account"           | (string)  | the account name of the receiving account                    |
| "amount"            | (numeric) | the total amount received by addresses with this account     |
| "confirmations"     | (numeric) | a confirmation number that is dPoW aware; see this [article](https://docs.komodoplatform.com/komodo/dPOW-conf.html) for more info |
| "rawconfirmations"  | (numeric) | the raw confirmations of the most recent transaction included (number of blocks on top of this transaction's block) |

#### 📌 Examples

Command:

```bash
./komodo-cli listreceivedbyaccount
```

Show Response

```json
[
  {
    "account": "",
    "amount": 0.000001,
    "rawconfirmations": 21,
    "confirmations": 21
  }
]
```

Command:

```bash
./komodo-cli listreceivedbyaccount 6 true
```

Show Response

```json
[
  {
    "account": "",
    "amount": 0.000001,
    "rawconfirmations": 23,
    "confirmations": 23
  }
]
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "listreceivedbyaccount", "params": [6, true, true] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": [
    {
      "account": "",
      "amount": 0.000001,
      "rawconfirmations": 24,
      "confirmations": 24
    }
  ],
  "error": null,
  "id": "curltest"
}
```