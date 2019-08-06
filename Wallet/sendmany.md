## sendmany

**sendmany "account" { "address": amount, ... } ( minconf "comment" [ "address", ... ] )**

The `sendmany` method can send multiple transactions at once. Amounts are double-precision floating point numbers.

### Arguments

| Name                                | Type                           | Description                                                  |
| ----------------------------------- | ------------------------------ | ------------------------------------------------------------ |
| "account"                           | (string, required)             | MUST be set to the empty string "" to represent the default account; passing any other string will result in an error |
| "amounts" { "address":amount, ... } | ("string":numeric)             | the address (string) and the value (double-precision floating numeric) |
| minconf                             | (numeric, optional, default=1) | only use the balance confirmed at least this many times      |
| "comment"                           | (string, optional)             | a comment                                                    |
| subtractfeefromamount               | (string, optional)             | a json array with addresses. The fee will be equally deducted from the amount of each selected address; the recipients will receive less than you enter in their corresponding amount field. If no addresses are specified here, the sender pays the fee. |
| "address"                           | (string)                       | subtract fee from this address                               |

### Response

| Name             | Type     | Description                                                  |
| ---------------- | -------- | ------------------------------------------------------------ |
| "transaction_id" | (string) | the transaction id for the send; only 1 transaction is created regardless of the number of addresses |

#### 📌 Examples

Command:

```bash
./komodo-cli sendmany "" '{"RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ":0.01,"RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu":0.02}'
```

Show Response

```bash
e39b046f0e30bd2a80c64ec78d902107858c8f0d55097d7f2293df1c9a4496ae
```

Command:

```bash
./komodo-cli sendmany "" '{"RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ":0.01,"RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu":0.02}' 6 "testing"
```

Show Response

```bash
3829164d8a68d9b7c2c89efe419eca77e37883318b7187b7e000e80e8138a370
```

Command:

```bash
./komodo-cli sendmany "" '{"RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ":0.01,"RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu":0.02}' 1 "" '["RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ","RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu"]'
```

Show Response

```bash
1813a39247913abf73af10ed51537234fe4e58eb5cfc4f49ac4fbcdecb42b4b4
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "sendmany", "params": ["", {"RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ":0.01,"RPS3xTZCzr6aQfoMw5Bu1rpQBF6iVCWsyu":0.02}, 6, "testing"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "fe7db27ed66b9d999c21d3cc9c8c687bd68721d711da6573a0a0ccf75c1cace5",
  "error": null,
  "id": "curltest"
}
```