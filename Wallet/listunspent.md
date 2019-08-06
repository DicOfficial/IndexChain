## listunspent

**listunspent ( minconf maxconf ["address", ... ] )**

The `listunspent` method returns an array of unspent transaction outputs, with a range between `minconf` and `maxconf` (inclusive) confirmations. The method can, optionally, filter to only include `txouts` paid to specified addresses.

### Arguments

| Name      | Type                                 | Description                         |
| --------- | ------------------------------------ | ----------------------------------- |
| minconf   | (numeric, optional, default=1)       | the minimum confirmations to filter |
| maxconf   | (numeric, optional, default=9999999) | the maximum confirmations to filter |
| "address" | (string)                             | a series of addresses               |

### Response

| Name               | Type      | Description                                                  |
| ------------------ | --------- | ------------------------------------------------------------ |
| "txid"             | (string)  | the transaction id                                           |
| "vout"             | (numeric) | the vout value                                               |
| "generated"        | (boolean) | true if txout is a coinbase transaction output               |
| "address"          | (string)  | the address                                                  |
| "account"          | (string)  | DEPRECATED the associated account, or "" for the default account |
| "scriptPubKey"     | (string)  | the script key                                               |
| "amount"           | (numeric) | the transaction amount                                       |
| "confirmations"    | (numeric) | a confirmation number that is dPoW aware; see this [article](https://docs.komodoplatform.com/komodo/dPOW-conf.html) for more info |
| "rawconfirmations" | (numeric) | the raw confirmations (number of blocks on top of this transaction's block) |

#### 📌 Examples

Command:

```bash
./komodo-cli listunspent
```

Show Response

```json
[
  {
    "txid": "269b658b9a52e9142c96f3a49c0ad917e5d0c08126baa96713827267137d150f",
    "vout": 0,
    "generated": true,
    "address": "RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu",
    "scriptPubKey": "21037e631c6a03d028e48aecfd93b2d2737d5d7e2852a426b940ff301f78aa31690cac",
    "amount": 0.00010000,
    "interest": 0.00000000,
    "rawconfirmations": 6,
    "confirmations": 1,
    "spendable": true
  },
    ...
]
```

Command:

```bash
./komodo-cli listunspent 6 9999999 '["RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu","RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ"]'
```

Show Response

```json
[
  {
    "txid": "0ca752c996c4074ca62071cdbf848ccd33864894151f982024006b3d69d021ac",
    "vout": 0,
    "generated": true,
    "address": "RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu",
    "scriptPubKey": "21037e631c6a03d028e48aecfd93b2d2737d5d7e2852a426b940ff301f78aa31690cac",
    "amount": 0.0001,
    "interest": 0.0,
    "rawconfirmations": 7,
    "confirmations": 1,
    "spendable": true
  },
  {
    "txid": "7281407d85619901ee10d52c96869f7879393434b782331df6f67a0e0e9d1ffa",
    "vout": 0,
    "generated": false,
    "address": "RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ",
    "scriptPubKey": "76a9141c973dbbed002e189caf31664d9ca7e8b1e92d8788ac",
    "amount": 9.99304496,
    "interest": 0.0,
    "rawconfirmations": 21,
    "confirmations": 21,
    "spendable": true
  }
]
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "listunspent", "params": [6, 9999999, ["RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu","RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ"]] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": [
    {
      "txid": "0ca752c996c4074ca62071cdbf848ccd33864894151f982024006b3d69d021ac",
      "vout": 0,
      "generated": true,
      "address": "RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu",
      "scriptPubKey": "21037e631c6a03d028e48aecfd93b2d2737d5d7e2852a426b940ff301f78aa31690cac",
      "amount": 0.0001,
      "interest": 0.0,
      "rawconfirmations": 7,
      "confirmations": 7,
      "spendable": true
    },
    {
      "txid": "7281407d85619901ee10d52c96869f7879393434b782331df6f67a0e0e9d1ffa",
      "vout": 0,
      "generated": false,
      "address": "RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ",
      "scriptPubKey": "76a9141c973dbbed002e189caf31664d9ca7e8b1e92d8788ac",
      "amount": 9.99304496,
      "interest": 0.0,
      "rawconfirmations": 21,
      "confirmations": 21,
      "spendable": true
    }
  ],
  "error": null,
  "id": "curltest"
}
```