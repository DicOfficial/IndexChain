## addmultisigaddress

**addmultisigaddress nrequired [ "key", ... ] ( "account" )**

The `addmultisigaddress` method adds a multi-signature address to the wallet, where `nrequired` indicates the number of keys (out of the total provided) required to execute a transaction.

The keys function as signatures, allowing multiple parties or entities to manage an account. Each key in the array can be an address or a hex-encoded public key.

DEPRECATED: If **account** is specified, the method assigns the multi-signature address to that account.

### Arguments

| Name         | Type                | Description                                                  |
| ------------ | ------------------- | ------------------------------------------------------------ |
| nrequired    | (numeric, required) | the number of required keys (out of the `n` submitted)       |
| "keysobject" | (string, required)  | a json array of addresses or hex-encoded public keys         |
| "address"    | (string)            | the address or hex-encoded public key                        |
| "account"    | (string, optional)  | DEPRECATED: if provided, "account" MUST be set to the empty string "" to represent the default account; passing any other string will result in an error |

### Response

| Name      | Type     | Description                         |
| --------- | -------- | ----------------------------------- |
| "address" | (string) | an address associated with the keys |

####  Examples

Add a multisig address from 2 addresses:

Command:

```bash
./komodo-cli addmultisigaddress 2 '["RSWwtqsNr9mW21UXRm6Lz4AzQnj4pVzzkp","RW8d8EChHTooVbwF3reqHYgkzWCnJFLXgh"]'
```

Show Response

```bash
bLz2YZ7Mm8MgPc9mPNiFqhjFPbFZU4WUD5
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "addmultisigaddress", "params": [2, ["RL4CuA2MSAbBiqJKQEr2TKnKT2fSwK99mG","RBYVFCxpJdLgvUixhguxzuH1TJpoNLYCJ6"]] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "bNdB9fAt9HmQD8CmBjkY6QwmrNSBrbzsgA",
  "error": null,
  "id": "curltest"
}
```