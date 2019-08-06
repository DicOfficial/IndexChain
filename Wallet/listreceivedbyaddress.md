## listreceivedbyaddress

**listreceivedbyaddress ( minconf includeempty includeWatchonly)**

The `listreceivedbyaddress` method lists balances by receiving address.

### Arguments

| Name             | Type                               | Description                                                  |
| ---------------- | ---------------------------------- | ------------------------------------------------------------ |
| minconf          | (numeric, optional, default=1)     | the minimum number of confirmations before payments are included |
| includeempty     | (numeric, optional, default=false) | whether to include addresses that haven't received any payments |
| includeWatchonly | (bool, optional, default=false)    | whether to include watchonly addresses (see 'importaddress') |

### Response

| Name                | Type      | Description                                                  |
| ------------------- | --------- | ------------------------------------------------------------ |
| "involvesWatchonly" | (bool)    | only returned if imported addresses were involved in transaction |
| "address"           | (string)  | the receiving address                                        |
| "account"           | (string)  | DEPRECATED the account of the receiving address; the default account is "" |
| "amount"            | (numeric) | the total amount received by the address                     |
| "confirmations"     | (numeric) | a confirmation number that is dPoW aware; see this [article](https://docs.komodoplatform.com/komodo/dPOW-conf.html) for more info |
| "rawconfirmations"  | (numeric) | the raw confirmations of the most recent transaction included (number of blocks on top of this transaction's block) |

#### 📌 Examples

Command:

```bash
./komodo-cli listreceivedbyaddress
```

Show Response

```json
[
  {
    "address": "RGmfyV6GLkNXTSM5XaxtpwPrw4R7iiHEa2",
    "account": "",
    "amount": 0.000001,
    "rawconfirmations": 40,
    "confirmations": 40,
    "txids": [
      "34efdb82ec718dede04feccecdc44f119cb7263f11c56ec3d7bf6234c9d0e27a"
    ]
  }
]
```

Command:

```bash
./komodo-cli listreceivedbyaddress 6 true
```

Show Response

```json
[
  {
    "address": "RGmfyV6GLkNXTSM5XaxtpwPrw4R7iiHEa2",
    "account": "",
    "amount": 0.000001,
    "rawconfirmations": 41,
    "confirmations": 41,
    "txids": [
      "34efdb82ec718dede04feccecdc44f119cb7263f11c56ec3d7bf6234c9d0e27a"
    ]
  },
  {
    "address": "RSMmyzk2cZ7xJdDx62wAZbvM5dzxH8CPqv",
    "account": "",
    "amount": 0.0,
    "rawconfirmations": 0,
    "confirmations": 0,
    "txids": []
  },
  {
    "address": "RVErfGzpdNSLrg19FVAuet6nXGDaWnqiVc",
    "account": "",
    "amount": 0.0,
    "rawconfirmations": 0,
    "confirmations": 0,
    "txids": []
  }
]
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "listreceivedbyaddress", "params": [6, true, true] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": [
    {
      "address": "RGmfyV6GLkNXTSM5XaxtpwPrw4R7iiHEa2",
      "account": "",
      "amount": 0.000001,
      "rawconfirmations": 41,
      "confirmations": 41,
      "txids": [
        "34efdb82ec718dede04feccecdc44f119cb7263f11c56ec3d7bf6234c9d0e27a"
      ]
    },
    {
      "address": "RSMmyzk2cZ7xJdDx62wAZbvM5dzxH8CPqv",
      "account": "",
      "amount": 0.0,
      "rawconfirmations": 0,
      "confirmations": 0,
      "txids": []
    },
    {
      "address": "RVErfGzpdNSLrg19FVAuet6nXGDaWnqiVc",
      "account": "",
      "amount": 0.0,
      "rawconfirmations": 0,
      "confirmations": 0,
      "txids": []
    }
  ],
  "error": null,
  "id": "curltest"
}
```