## setaccount

**setaccount "address" "account"**

Notice

DEPRECATED

The `setaccount` method sets the account associated with the given address.

### Arguments

| Name      | Type               | Description                                                  |
| --------- | ------------------ | ------------------------------------------------------------ |
| "address" | (string, required) | the address to be associated with an account                 |
| "account" | (string, required) | MUST be set to the empty string "" to represent the default account; passing any other string will result in an error |

#### 📌 Examples

Command:

```bash
./komodo-cli setaccount "RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ" "tabby"
```

Show Response

```bash
(deprecated)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "setaccount", "params": ["RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ", "tabby"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```bash
(deprecated)
```