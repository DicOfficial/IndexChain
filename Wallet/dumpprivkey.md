## dumpprivkey

**dumpprivkey "address"**

The `dumpprivkey` method reveals the private key corresponding to the indicated `address`.

See also **importprivkey**.

### Arguments

| Name      | Type               | Description                     |
| --------- | ------------------ | ------------------------------- |
| "address" | (string, required) | the address for the private key |

### Response

| Name   | Type     | Description     |
| ------ | -------- | --------------- |
| "data" | (string) | the private key |

#### 📌 Examples

Command:

```bash
./komodo-cli dumpprivkey "RTcwYaQPDVN7V9SdfFHARWnoB7vcpSfdvs"
```

Show Response

```bash
DONOTUSExxxxxxxxxxxxxxxxxxxx4KkCmRnnSg7iXvAUjoYivC8K
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "dumpprivkey", "params": ["RTcwYaQPDVN7V9SdfFHARWnoB7vcpSfdvs"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "DONOTUSExxxxxxxxxxxxxxxxxxxx4KkCmRnnSg7iXvAUjoYivC8K",
  "error": null,
  "id": "curltest"
}
```