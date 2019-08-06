## getaccount

**getaccount "address"**

The `getaccount` method returns the account associated with the given address.

### Arguments

| Name      | Type               | Description |
| --------- | ------------------ | ----------- |
| "address" | (string, required) | the address |

### Response

| Name          | Type     | Description         |
| ------------- | -------- | ------------------- |
| "accountname" | (string) | the account address |

#### 📌 Examples

Command:

```bash
./komodo-cli getaccount "RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ"
```

Show Response

```bash
(deprecated)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getaccount", "params": ["RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```bash
(deprecated)
```