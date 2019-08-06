## z_listreceivedbyaddress

**z_listreceivedbyaddress "address" ( minconf )**

The `z_listreceivedbyaddress` method returns a list of amounts received by a z address belonging to the node’s wallet.

### Arguments

| Name    | Type                           | Description                                                  |
| ------- | ------------------------------ | ------------------------------------------------------------ |
| address | (string)                       | the private address.                                         |
| minconf | (numeric, optional, default=1) | only include transactions confirmed at least this many times |

### Result

An array of json objects, each having the properties below.

| Name               | Type                                         | Description                                                  |
| ------------------ | -------------------------------------------- | ------------------------------------------------------------ |
| txid               | (string)                                     | the transaction id                                           |
| amount             | (numeric)                                    | the amount of value in the note                              |
| memo               | (string)                                     | hexadecimal string representation of memo field              |
| "confirmations"    | (numeric)                                    | a confirmation number that is dPoW aware; see this [article](https://docs.komodoplatform.com/komodo/dPOW-conf.html) for more info |
| "rawconfirmations" | (numeric)                                    | the raw confirmations (number of blocks on top of this transaction's block) |
| jsindex            | (sprout)                                     | (numeric, received only by sprout addresses) the joinsplit index |
| jsoutindex         | (numeric, received only by sprout addresses) | the output index of the joinsplit                            |
| outindex           | (numeric, sapling)                           | the output index                                             |
| change             | (boolean)                                    | true if the address that received the note is also one of the sending addresses |

#### 📌 Examples

Command:

```bash
./komodo-cli z_listreceivedbyaddress "zs1wqykmk74mv2ezjscpxsgzrn4fasqwh50tgk0ym64m45c5yw5fjtpkps64gle963veqzuj04872z"
```

Show Response

```bash
[
  {
    "txid": "b9a98f3cbfec7a8a93c240e19e8eea5ab3ee8de3e6372105ffb72308b72ea05f",
    "amount": 77.00000000,
    "memo": "f600000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "outindex": 0,
    "rawconfirmations": 9,
    "confirmations": 9,
    "change": false
  }
]
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user rpcuser:rpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_listreceivedbyaddress", "params": ["zs1umhaattx6lna933m9zwfqlmkm2qj49hpa9lnymtj5h5c7cwtd3evfpu29hppprax9cs45fzeyqg"] }' -H 'content-type: text/plain;' http://127.0.0.1:rpcport/
```

Show Response

```bash
blockHash 0a4f15fe5425ef8bc6eb84e7bc3625c1ceccb3e49132b696a1841ab17a75a705 height 55200
{"result":[{"txid":"23d33c0c12ba2224b2c9c252e304f491bf76ca05670c8f00d48300776c10850f","amount":100.00
```