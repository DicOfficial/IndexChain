## z_listunspent

**z_listunspent ( minconf maxconf includeWatchonly ["zaddr", ...] )**

The `z_listunspent` method returns an array of unspent shielded notes.

The method can also filter to only include results that have between `minconf` and `maxconf`(inclusive) confirmations, and also for specified z_addresses (`["zaddr", ...])`.

When `minconf` is `0` unspent notes with zero confirmations are returned, even though they are not immediately spendable.

Results are an array of Objects, each of which has: {txid, jsindex, jsoutindex, confirmations, address, amount, memo} (Sprout) {txid, outindex, confirmations, address, amount, memo} (Sapling)

### Arguments

| Name             | Type                                 | Description                                                  |
| ---------------- | ------------------------------------ | ------------------------------------------------------------ |
| minconf          | (numeric, optional, default=1)       | the minimum confirmations to filter                          |
| maxconf          | (numeric, optional, default=9999999) | the maximum confirmations to filter                          |
| includeWatchonly | (bool, optional, default=false)      | whether to also include watchonly addresses (see [z_importviewingkey](https://docs.komodoplatform.com/basic-docs/komodo-api/wallet.html#z-importviewingkey)) |
| addresses        | (array)                              | a json array of z addresses (both Sprout and Sapling) to act as a filter; duplicate addresses are not allowed |
| address          | (string)                             | a z address                                                  |

### Results

An array of json objects, each having the properties below.

| Name               | Type                                          | Description                                                  |
| ------------------ | --------------------------------------------- | ------------------------------------------------------------ |
| txid               | (string)                                      | the transaction id                                           |
| jsindex            | (numeric)                                     | the joinsplit index                                          |
| jsoutindex         | (numeric, only returned on sprout addresses)  | the output index of the joinsplit                            |
| outindex           | (numeric, only returned on sapling addresses) | the output index                                             |
| "confirmations"    | (numeric)                                     | a confirmation number that is dPoW aware; see this [article](https://docs.komodoplatform.com/komodo/dPOW-conf.html) for more info |
| "rawconfirmations" | (numeric)                                     | the raw confirmations (number of blocks on top of this transaction's block) |
| spendable          | (boolean)                                     | true if note can be spent by wallet, false if note has zero confirmations, false if address is watchonly |
| address            | (string)                                      | the shielded address                                         |
| amount             | (numeric)                                     | the amount of value in the note                              |
| memo               | (string)                                      | hexadecimal string representation of memo field              |
| change             | (boolean)                                     | true if the address that received the note is also one of the sending addresses |

#### 📌 Examples

Command:

```text
./komodo-cli z_listunspent
```

Show Response

```bash
[
  {
    "txid": "b9a98f3cbfec7a8a93c240e19e8eea5ab3ee8de3e6372105ffb72308b72ea05f",
    "outindex": 0,
    "confirmations": 1,
    "rawconfirmations": 1,
    "spendable": true,
    "address": "zs1wqykmk74mv2ezjscpxsgzrn4fasqwh50tgk0ym64m45c5yw5fjtpkps64gle963veqzuj04872z",
    "amount": 77.00000000,
    "memo": "f600000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "change": false
  }
]
```

Command:

```bash
./komodo-cli -ac_name=BEER z_listunspent 1 100 false "[\"zs1wqykmk74mv2ezjscpxsgzrn4fasqwh50tgk0ym64m45c5yw5fjtpkps64gle963veqzuj04872z\"]"
```

Show Response

```bash
[
  {
    "txid": "b9a98f3cbfec7a8a93c240e19e8eea5ab3ee8de3e6372105ffb72308b72ea05f",
    "outindex": 0,
    "confirmations": 2,
    "rawconfirmations": 2,
    "spendable": true,
    "address": "zs1wqykmk74mv2ezjscpxsgzrn4fasqwh50tgk0ym64m45c5yw5fjtpkps64gle963veqzuj04872z",
    "amount": 77.00000000,
    "memo": "f600000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "change": false
  }
]
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user rpcuser:rpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_listunspent", "params": [1, 9999999, false, ["zs1umhaattx6lna933m9zwfqlmkm2qj49hpa9lnymtj5h5c7cwtd3evfpu29hppprax9cs45fzeyqg"] ] }' -H 'content-type: text/plain;' http://127.0.0.1:rpcport/
```

Show Response

```bash
blockHash 0a4f15fe5425ef8bc6eb84e7bc3625c1ceccb3e49132b696a1841ab17a75a705 height 55200
{"result":[{"txid":"23d33c0c12ba2224b2c9c252e304f491bf76ca05670c8f00d48300776c10850f","outindex":0,"confirm
```