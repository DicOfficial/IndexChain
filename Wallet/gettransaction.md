## gettransaction

**gettransaction "txid" ( includeWatchonly )**

The `gettransaction` method queries detailed information about transaction `txid`. This command applies only to `txid`'s that are in the user's local wallet.

### Arguments

| Name               | Type                            | Description                                                  |
| ------------------ | ------------------------------- | ------------------------------------------------------------ |
| "txid"             | (string, required)              | the transaction id                                           |
| "includeWatchonly" | (bool, optional, default=false) | whether to include watchonly addresses in the returned balance calculation and in the `details[]` returned values |

### Response

| Name                    | Type                    | Description                                                  |
| ----------------------- | ----------------------- | ------------------------------------------------------------ |
| "amount"                | (numeric)               | the transaction amount                                       |
| "confirmations"         | (numeric)               | a confirmation number that is dPoW aware; see this [article](https://docs.komodoplatform.com/komodo/dPOW-conf.html) for more info |
| "rawconfirmations"      | (numeric)               | the raw confirmations (number of blocks on top of this transaction's block) |
| "blockhash"             | (string)                | the block hash                                               |
| "blockindex"            | (numeric)               | the block index                                              |
| "blocktime"             | (numeric)               | the time in seconds since epoch (1 Jan 1970 GMT)             |
| "txid"                  | (string)                | the transaction id                                           |
| "time"                  | (numeric)               | the transaction time in seconds since epoch (1 Jan 1970 GMT) |
| "timereceived"          | (numeric)               | the time received in seconds since epoch (1 Jan 1970 GMT)    |
| "details" : [ ... ]     | (array)                 |                                                              |
| "account"               | (string)                | DEPRECATED the account name involved in the transaction; can be "" for the default account |
| "address"               | (string)                | the address involved in the transaction                      |
| "category"              | (string)                | the category - either `send` or `receive`                    |
| "amount"                | (numeric)               | the amount                                                   |
| "vout"                  | (numeric)               | the vout value                                               |
| "vjoinsplit" : [ ... ]  | (array of json objects) |                                                              |
| "anchor"                | (string)                | merkle root of note commitment tree                          |
| "nullifiers" : [ ... ]  | (array of strings)      |                                                              |
| "hex"                   | (string)                |                                                              |
| "commitments" : [ ... ] | (array of strings)      |                                                              |
| "hex"                   | (string)                |                                                              |
| "macs" : [ ... ]        | (array of strings)      |                                                              |
| "hex"                   | (string)                |                                                              |
| "vpub_old"              | (numeric)               | the amount removed from the transparent value pool           |
| "vpub_new"              | (numeric)               | the amount added to the transparent value pool               |
| "hex"                   | (string)                | transaction data translated into hex                         |

#### 📌 Examples

Command:

```bash
./komodo-cli gettransaction "34efdb82ec718dede04feccecdc44f119cb7263f11c56ec3d7bf6234c9d0e27a"
```

Show Response

```json
{
  "amount": 0.000001,
  "rawconfirmations": 14,
  "confirmations": 1,
  "blockhash": "07eb80d845eae646a95351a47a1b54964610f3caf4d4ff53750d0de66fbfc525",
  "blockindex": 1,
  "blocktime": 1552585479,
  "expiryheight": 1268793,
  "txid": "34efdb82ec718dede04feccecdc44f119cb7263f11c56ec3d7bf6234c9d0e27a",
  "walletconflicts": [],
  "time": 1552585444,
  "timereceived": 1552585444,
  "vjoinsplit": [],
  "details": [
    {
      "account": "",
      "address": "RGmfyV6GLkNXTSM5XaxtpwPrw4R7iiHEa2",
      "category": "receive",
      "amount": 0.000001,
      "vout": 1,
      "size": 254
    }
  ],
  "hex": "0400008085202f8901310bd18e1c5de58eed0482e13c855763e83fadb19c1abd330e62c07a13370edf1b0000006a47304402207a607ff3b479317dd41842f024380994ec7e4353c0cb33bff32bc795cfa8a7c202205ff036aeee1760f0677d22155be8210b78ffffb3b03f568304278a914fe6e0d1012103336ca9db27cb6e882830e20dc525884e27dc94d557a5e68b972a5cbf9e8c62a8feffffff0254738e1d00000000232103336ca9db27cb6e882830e20dc525884e27dc94d557a5e68b972a5cbf9e8c62a8ac64000000000000001976a914522bd057d4304d6204187c99e6dece0c29bdbe9788acce928a5c395c13000000000000000000000000"
}
```

Command:

```bash
./komodo-cli gettransaction "34efdb82ec718dede04feccecdc44f119cb7263f11c56ec3d7bf6234c9d0e27a" true
```

Show Response

```json
{
  "amount": 0.000001,
  "rawconfirmations": 14,
  "confirmations": 1,
  "blockhash": "07eb80d845eae646a95351a47a1b54964610f3caf4d4ff53750d0de66fbfc525",
  "blockindex": 1,
  "blocktime": 1552585479,
  "expiryheight": 1268793,
  "txid": "34efdb82ec718dede04feccecdc44f119cb7263f11c56ec3d7bf6234c9d0e27a",
  "walletconflicts": [],
  "time": 1552585444,
  "timereceived": 1552585444,
  "vjoinsplit": [],
  "details": [
    {
      "account": "",
      "address": "RGmfyV6GLkNXTSM5XaxtpwPrw4R7iiHEa2",
      "category": "receive",
      "amount": 0.000001,
      "vout": 1,
      "size": 254
    }
  ],
  "hex": "0400008085202f8901310bd18e1c5de58eed0482e13c855763e83fadb19c1abd330e62c07a13370edf1b0000006a47304402207a607ff3b479317dd41842f024380994ec7e4353c0cb33bff32bc795cfa8a7c202205ff036aeee1760f0677d22155be8210b78ffffb3b03f568304278a914fe6e0d1012103336ca9db27cb6e882830e20dc525884e27dc94d557a5e68b972a5cbf9e8c62a8feffffff0254738e1d00000000232103336ca9db27cb6e882830e20dc525884e27dc94d557a5e68b972a5cbf9e8c62a8ac64000000000000001976a914522bd057d4304d6204187c99e6dece0c29bdbe9788acce928a5c395c13000000000000000000000000"
}
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "gettransaction", "params": ["34efdb82ec718dede04feccecdc44f119cb7263f11c56ec3d7bf6234c9d0e27a"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": {
    "amount": 0.000001,
    "rawconfirmations": 19,
    "confirmations": 1,
    "blockhash": "07eb80d845eae646a95351a47a1b54964610f3caf4d4ff53750d0de66fbfc525",
    "blockindex": 1,
    "blocktime": 1552585479,
    "expiryheight": 1268793,
    "txid": "34efdb82ec718dede04feccecdc44f119cb7263f11c56ec3d7bf6234c9d0e27a",
    "walletconflicts": [],
    "time": 1552585444,
    "timereceived": 1552585444,
    "vjoinsplit": [],
    "details": [
      {
        "account": "",
        "address": "RGmfyV6GLkNXTSM5XaxtpwPrw4R7iiHEa2",
        "category": "receive",
        "amount": 0.000001,
        "vout": 1,
        "size": 254
      }
    ],
    "hex": "0400008085202f8901310bd18e1c5de58eed0482e13c855763e83fadb19c1abd330e62c07a13370edf1b0000006a47304402207a607ff3b479317dd41842f024380994ec7e4353c0cb33bff32bc795cfa8a7c202205ff036aeee1760f0677d22155be8210b78ffffb3b03f568304278a914fe6e0d1012103336ca9db27cb6e882830e20dc525884e27dc94d557a5e68b972a5cbf9e8c62a8feffffff0254738e1d00000000232103336ca9db27cb6e882830e20dc525884e27dc94d557a5e68b972a5cbf9e8c62a8ac64000000000000001976a914522bd057d4304d6204187c99e6dece0c29bdbe9788acce928a5c395c13000000000000000000000000"
  },
  "error": null,
  "id": "curltest"
}
```