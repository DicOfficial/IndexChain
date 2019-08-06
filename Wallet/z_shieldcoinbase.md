## z_shieldcoinbase

**z_shieldcoinbase "fromaddress" "tozaddress" ( fee ) ( limit )**

The `z_shieldcoinbase` method shields transparent coinbase funds by sending the funds to a shielded z address. This is an asynchronous operation and utxos selected for shielding will be locked. If there is an error, they are unlocked.

The RPC call `listlockunspent` can be used to return a list of locked utxos. The number of coinbase utxos selected for shielding can be limited by the caller. If the limit parameter is set to zero, the [mempooltxinputlimit](https://docs.komodoplatform.com/basic-docs/installations/common-runtime-parameters.html#mempooltxinputlimit) option will determine the number of uxtos. Any limit is constrained by the consensus rule defining a maximum transaction size of 100000 bytes.

### [Arguments

| Name          | Type                                | Description                                                  |
| ------------- | ----------------------------------- | ------------------------------------------------------------ |
| "fromaddress" | (string, required)                  | the address is a t address or `"*"` for all t address belonging to the wallet |
| "toaddress"   | (string, required)                  | the address is a z address                                   |
| fee           | (numeric, optional, default=0.0001) | the fee amount to attach to this transaction                 |
| limit         | (numeric, optional, default=50)     | limit on the maximum number of utxos to shield; set to `0` to use node option `mempooltxinputlimit` |

### Response

| Name             | Type      | Description                                                  |
| ---------------- | --------- | ------------------------------------------------------------ |
| "remainingUTXOs" | (numeric) | the number of coinbase utxos still available for shielding   |
| "remainingValue" | (numeric) | the value of coinbase utxos still available for shielding    |
| "shieldingUTXOs" | (numeric) | the number of coinbase utxos being shielded                  |
| "shieldingValue" | (numeric) | the value of coinbase utxos being shielded                   |
| "opid"           | (string)  | an operationid to pass to z_getoperationstatus to get the result of the operation |

#### 📌 Examples

Command:

```bash
./komodo-cli z_shieldcoinbase "RXN2rxidK4cwzRL44UTnWvQjjvLdoMmCpU" "ztYMDvwUqi5FZLQy4so71ZGHXk2fDtEYU9HNns9DNYjXJr9PEzSL8Dq8NcdiRijsgCm4r3nNWA6dUrqW9suGd2F7uuj2BhP"
```

Show Response

```json
{
  "remainingUTXOs": 0,
  "remainingValue": 0.0,
  "shieldingUTXOs": 2,
  "shieldingValue": 0.0003,
  "opid": "opid-c0a7875c-aaa0-4bdc-8f17-b34ab99e8bab"
}
```

Command:

```bash
./komodo-cli z_shieldcoinbase "REyaj53EB2nwUnsmVyn8JHCcquKf1zYkEP" "ztYMDvwUqi5FZLQy4so71ZGHXk2fDtEYU9HNns9DNYjXJr9PEzSL8Dq8NcdiRijsgCm4r3nNWA6dUrqW9suGd2F7uuj2BhP" 0.0001 50
```

Show Response

```json
{
  "remainingUTXOs": 0,
  "remainingValue": 0.0,
  "shieldingUTXOs": 14,
  "shieldingValue": 0.0016,
  "opid": "opid-08ce931d-876c-45d5-9aea-15cf4c695e72"
}
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_shieldcoinbase", "params": ["RWRSfEYcfLv3yy9mhAuKHQTMCs9fArpPiH", "ztYMDvwUqi5FZLQy4so71ZGHXk2fDtEYU9HNns9DNYjXJr9PEzSL8Dq8NcdiRijsgCm4r3nNWA6dUrqW9suGd2F7uuj2BhP"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": {
    "remainingUTXOs": 0,
    "remainingValue": 0,
    "shieldingUTXOs": 1,
    "shieldingValue": 0.00025,
    "opid": "opid-53018a85-cf68-4e7d-a065-0defea6bf061"
  },
  "error": null,
  "id": "curltest"
}
```