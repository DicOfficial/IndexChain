## getaddressesbyaccount

**getaddressesbyaccount "account"**

DEPRECATED

The `getaddressesbyaccount` method returns the list of addresses for the given `account`.

### Arguments

| Name      | Type               | Description                                                  |
| --------- | ------------------ | ------------------------------------------------------------ |
| "account" | (string, required) | MUST be set to the empty string "" to represent the default account; passing any other string will result in an error |

### Response

| Name      | Type     | Description                                  |
| --------- | -------- | -------------------------------------------- |
| "address" | (string) | an address associated with the given account |

#### 📌 Examples

Command:

```bash
./komodo-cli getaddressesbyaccount "tabby"
```

Show Response

```bash
(deprecated)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getaddressesbyaccount", "params": ["tabby"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```bash
(deprecated)
```