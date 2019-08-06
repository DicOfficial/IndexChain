## z_mergetoaddress

**z_mergetoaddress [ "fromaddress", ... ] "toaddress" ( fee ) ( transparent_limit ) ( shielded_limit ) ( memo )**

CAUTION: **z_mergetoaddress** is DISABLED but can be enabled as an experimental feature.

The `z_mergetoaddress` method merges multiple utxos and notes into a single utxo or note. The method works for both t addresses and z addresses, both separately and in combination. Coinbase utxos are ignored; use `z_shieldcoinbase` to combine those into a single note.

This is an asynchronous operation, and utxos selected for merging will be locked. If there is an error, they are unlocked. The RPC call `listlockunspent` can be used to return a list of locked utxos.

The number of utxos and notes selected for merging can be limited by the caller. If the transparent limit parameter is set to `0`, the `mempooltxinputlimit` option will determine the number of utxos. Any limit is constrained by the consensus rule defining a maximum transaction size of 100000 bytes.

### The fromaddresses array

The following special strings are accepted inside the `fromaddresses` array:

- `"*"`: Merge both utxos and notes from all addresses belonging to the wallet
- `"ANY_TADDR"`: Merge utxos from all t addresses belonging to the wallet
- `"ANY_ZADDR"`: Merge notes from all z addresses belonging to the wallet

If a special string is given, any given addresses of that type will be ignored

### Arguments

| Name              | Type                                | Description                                                  |
| ----------------- | ----------------------------------- | ------------------------------------------------------------ |
| fromaddresses     | (string, required)                  |                                                              |
| "address"         | (string)                            | can be a t address or a z address                            |
| "toaddress"       | (string, required)                  | the t address or z address to receive the combined utxo      |
| fee               | (numeric, optional, default=0.0001) | the fee amount to attach to this transaction                 |
| transparent_limit | (numeric, optional, default=50)     | limit on the maximum number of transparent utxos to merge; you may set this value to 0 to use the node option [mempooltxinputlimit](https://docs.komodoplatform.com/basic-docs/installations/common-runtime-parameters.html#mempooltxinputlimit) |
| shielded_limit    | (numeric, optional, default=10)     | limit on the maximum number of hidden notes to merge; you may set this value to 0 to merge as many as will fit in the transaction |
| "memo"            | (string, optional)                  | encoded as hex; when `toaddress` is a z address, this value will be stored in the memo field of the new note |

### Response

| Name                        | Type      | Description                                                  |
| --------------------------- | --------- | ------------------------------------------------------------ |
| "remainingUTXOs"            | (numeric) | the number of utxos still available for merging              |
| "remainingTransparentValue" | (numeric) | the value of utxos still available for merging               |
| "remainingNotes"            | (numeric) | the number of notes still available for merging              |
| "remainingShieldedValue"    | (numeric) | the value of notes still available for merging               |
| "mergingUTXOs"              | (numeric) | the number of utxos being merged                             |
| "mergingTransparentValue"   | (numeric) | the value of utxos being merged                              |
| "mergingNotes"              | (numeric) | the number of notes being merged                             |
| "mergingShieldedValue"      | (numeric) | the value of notes being merged                              |
| "opid"                      | (string)  | an operationid to pass to `z_getoperationstatus` to get the result of the operation |

#### 📌 Examples

Command:

```bash
./komodo-cli z_mergetoaddress '["t1M72Sfpbz1BPpXFHz9m3CdqATR44Jvaydd"]' ztfaW34Gj9FrnGUEf833ywDVL62NWXBM81u6EQnM6VR45eYnXhwztecW1SjxA7JrmAXKJhxhj3vDNEpVCQoSvVoSpmbhtjf
```

Show Response

```bash
(disabled)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_mergetoaddress", "params": [["t1M72Sfpbz1BPpXFHz9m3CdqATR44Jvaydd"], "ztfaW34Gj9FrnGUEf833ywDVL62NWXBM81u6EQnM6VR45eYnXhwztecW1SjxA7JrmAXKJhxhj3vDNEpVCQoSvVoSpmbhtjf"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```bash
(disabled)
```