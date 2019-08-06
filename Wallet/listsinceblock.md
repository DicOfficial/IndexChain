## listsinceblock

**listsinceblock ( "blockhash" target-confirmations includeWatchonly )**

The `listsinceblock` method queries all transactions in blocks since block `blockhash`, or all transactions if `blockhash` is omitted.

### Arguments

| Name                 | Type                            | Description                                                  |
| -------------------- | ------------------------------- | ------------------------------------------------------------ |
| "blockhash"          | (string, optional)              | the block hash from which to list transactions               |
| target-confirmations | (numeric, optional)             | the confirmations required (must be 1 or more)               |
| includeWatchonly     | (bool, optional, default=false) | include transactions to watchonly addresses (see also 'importaddress') |

### Response

| Name               | Type      | Description                                                  |
| ------------------ | --------- | ------------------------------------------------------------ |
| "transactions":    |           |                                                              |
| "account"          | (string)  | DEPRECATED the account name associated with the transaction; will be "" for the default account |
| "address"          | (string)  | the address of the transaction (not present for move transactions -- category = move) |
| "category"         | (string)  | the transaction category; `send` has negative amounts, `receive` has positive amounts |
| "amount"           | (numeric) | the amount of the relevant currency -- negative for the `send` category, and for the `move` category for moves outbound. It is positive for the `receive`category, and for the `move` category for inbound funds. |
| "vout"             | (numeric) | the vout value                                               |
| "fee"              | (numeric) | the amount of the fee; this value is negative and only available for the `send` category of transactions |
| "confirmations"    | (numeric) | a confirmation number that is dPoW aware; see this [article](https://docs.komodoplatform.com/komodo/dPOW-conf.html) for more info |
| "rawconfirmations" | (numeric) | the raw confirmations of the transaction; available for `send` and `receive` category of transactions (number of blocks on top of this transaction's block) |
| "blockhash"        | (string)  | the block hash containing the transaction; available for the `send` and `receive` categories of transactions |
| "blockindex"       | (numeric) | the block index containing the transaction; available for the `send` and `receive` categories of transactions |
| "blocktime"        | (numeric) | the block time in seconds since epoch (1 Jan 1970 GMT)       |
| "txid"             | (string)  | the transaction id; available for `send` and `receive`categories of transactions |
| "time"             | (numeric) | the transaction time in seconds since epoch (Jan 1 1970 GMT) |
| "timereceived"     | (numeric) | the time received in seconds since epoch (Jan 1 1970 GMT); available for `send` and `receive`category of transactions |
| "comment"          | (string)  | whether a comment is associated with the transaction         |
| "to"               | (string)  | whether a 'to' comment is associated with the transaction    |
| "lastblock"        | (string)  | the hash of the last block                                   |

#### 📌 Examples

Command:

```bash
./komodo-cli listsinceblock
```

Show Response

```json
{
  "transactions": [
    {
      "account": "",
      "address": "RGmfyV6GLkNXTSM5XaxtpwPrw4R7iiHEa2",
      "category": "receive",
      "amount": 0.000001,
      "vout": 1,
      "rawconfirmations": 44,
      "confirmations": 44,
      "blockhash": "07eb80d845eae646a95351a47a1b54964610f3caf4d4ff53750d0de66fbfc525",
      "blockindex": 1,
      "blocktime": 1552585479,
      "expiryheight": 1268793,
      "txid": "34efdb82ec718dede04feccecdc44f119cb7263f11c56ec3d7bf6234c9d0e27a",
      "walletconflicts": [],
      "time": 1552585444,
      "timereceived": 1552585444,
      "vjoinsplit": [],
      "size": 254
    }
  ],
  "lastblock": "05686392a3011a180988246b3b0343bc4eec992c101d2e651c6ee786af1b2fb5"
}
```

Command:

```bash
./komodo-cli listsinceblock "029f11d80ef9765602235e1bc9727e3eb6ba20839319f761fee920d63401e327" 6
```

Show Response

```json
{
  "transactions": [
    {
      "account": "",
      "address": "RGmfyV6GLkNXTSM5XaxtpwPrw4R7iiHEa2",
      "category": "receive",
      "amount": 0.000001,
      "vout": 1,
      "rawconfirmations": 45,
      "confirmations": 45,
      "blockhash": "07eb80d845eae646a95351a47a1b54964610f3caf4d4ff53750d0de66fbfc525",
      "blockindex": 1,
      "blocktime": 1552585479,
      "expiryheight": 1268793,
      "txid": "34efdb82ec718dede04feccecdc44f119cb7263f11c56ec3d7bf6234c9d0e27a",
      "walletconflicts": [],
      "time": 1552585444,
      "timereceived": 1552585444,
      "vjoinsplit": [],
      "size": 254
    }
  ],
  "lastblock": "08db1a09b32ebb55f026c41d5555281ebeae4c9eb8b36e88db62b6f1d7fd12d1"
}
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "listsinceblock", "params": ["029f11d80ef9765602235e1bc9727e3eb6ba20839319f761fee920d63401e327", 6] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": {
    "transactions": [
      {
        "account": "",
        "address": "RGmfyV6GLkNXTSM5XaxtpwPrw4R7iiHEa2",
        "category": "receive",
        "amount": 0.000001,
        "vout": 1,
        "rawconfirmations": 46,
        "confirmations": 46,
        "blockhash": "07eb80d845eae646a95351a47a1b54964610f3caf4d4ff53750d0de66fbfc525",
        "blockindex": 1,
        "blocktime": 1552585479,
        "expiryheight": 1268793,
        "txid": "34efdb82ec718dede04feccecdc44f119cb7263f11c56ec3d7bf6234c9d0e27a",
        "walletconflicts": [],
        "time": 1552585444,
        "timereceived": 1552585444,
        "vjoinsplit": [],
        "size": 254
      }
    ],
    "lastblock": "01b4ce6c4659138de1a7a67e8dac354b5acc3a998145effedbfec7ef41a2cec6"
  },
  "error": null,
  "id": "curltest"
}
```