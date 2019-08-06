## getaccountaddress

**getaccountaddress "account"**

DEPRECATED

The `getaccountaddress` method returns the current address for receiving payments to this account.

### Arguments

| Name      | Type               | Description                                                  |
| --------- | ------------------ | ------------------------------------------------------------ |
| "account" | (string, required) | MUST be set to the empty string "" to represent the default account; passing any other string will result in an error |

### Response

| Name      | Type     | Description         |
| --------- | -------- | ------------------- |
| "address" | (string) | the account address |

#### 📌 Examples

Command:

```bash
./komodo-cli getaccountaddress
```

Hide Response

```bash
(deprecated)
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getaccountaddress", "params": ["myaccount"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Hide Response

```bash
(deprecated)
```