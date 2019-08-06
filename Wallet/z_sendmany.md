## z_sendmany

**z_sendmany "fromaddress" [ { "address": ..., "amount": ... }, ... ] ( minconf ) ( fee )**

The `z_sendmany` method sends one or more transactions at once, and allows for sending transactions of types `t --> t`, `t --> z`, `z --> z`, `z --> t`. It is the principle method for dealing with shielded `z` transactions in the Komodo ecosystem.

The `amount` values are double-precision floating point numbers. Change from a t address flows to a new t address address, while change from z address returns to itself. When sending coinbase utxos to a z address, change is not allowed. The entire value of the utxo(s) must be consumed. Currently, the maximum number of z address outputs is 54 due to transaction-size limits.

### Arguments

| Name          | Type                                | Description                                                  |
| ------------- | ----------------------------------- | ------------------------------------------------------------ |
| "fromaddress" | (string, required)                  | the sending t address or z address                           |
| "amounts"     | (array of json objects)             |                                                              |
| "address"     | (string, required)                  | the receiving address; can be a t address or z address       |
| "amount"      | (numeric, required)                 | the numeric amount                                           |
| "memo"        | (string, optional)                  | if the address is a z address, this property accepts raw data represented in hexadecimal string format |
| minconf       | (numeric, optional, default=1)      | only use funds confirmed at least this many times            |
| fee           | (numeric, optional, default=0.0001) | the fee amount to attach to this transaction                 |

### Response

| Name          | Type     | Description                                                  |
| ------------- | -------- | ------------------------------------------------------------ |
| "operationid" | (string) | an operationid to pass to z_getoperationstatus to get the result of the operation |

#### 📌 Examples

Command:

```bash
./komodo-cli z_sendmany "RUX5vGkxJCKBPGm8b97VUumt2aHkuCjp8e" '[{"address":"RVEsww91UBdUNGyCC1GjDVuvJShEei2kj4","amount":0.01}]'
```

Show Response

```bash
opid-ad947755-b348-4842-90ca-0f0c71d13d34
```

Command:

```bash
./komodo-cli z_sendmany "RCpMUZwxc3pWsgip5aj3Sy1cKkh86P3Tns" '[{"address":"ztci8RzNSo2pdiDpAeHpz9Rp91hq12Mn7zcFfBR8Jjs2ydZUCTw8rLZzkVP888M4vGezpZVfsTR8orgxYK3N8gdgbBzakx3","amount":0.01}]'
```

Show Response

```bash
opid-cdd6af37-88a2-44d7-9630-d54d21f8b1c4
```

Command:

```bash
./komodo-cli z_sendmany "ztci8RzNSo2pdiDpAeHpz9Rp91hq12Mn7zcFfBR8Jjs2ydZUCTw8rLZzkVP888M4vGezpZVfsTR8orgxYK3N8gdgbBzakx3" '[{"address":"ztYMDvwUqi5FZLQy4so71ZGHXk2fDtEYU9HNns9DNYjXJr9PEzSL8Dq8NcdiRijsgCm4r3nNWA6dUrqW9suGd2F7uuj2BhP","amount":0.0099}]'
```

Show Response

```bash
opid-3c3d6f25-f333-4898-8a50-06f4012cf975
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "z_sendmany", "params": ["RCpMUZwxc3pWsgip5aj3Sy1cKkh86P3Tns", [{"address": "ztfaW34Gj9FrnGUEf833ywDVL62NWXBM81u6EQnM6VR45eYnXhwztecW1SjxA7JrmAXKJhxhj3vDNEpVCQoSvVoSpmbhtjf" ,"amount": 0.01}]] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```bash
{
  "result": "opid-73306924-3466-4944-a8f7-c45c14be0438",
  "error": null,
  "id": "curltest"
}
```