## getreceivedbyaddress

**getreceivedbyaddress "address" ( minconf )**

The `getreceivedbyaddress` method returns the total amount received by the given `address` in transactions with at least `minconf` confirmations.

### Arguments

| Name      | Type                           | Description                                                  |
| --------- | ------------------------------ | ------------------------------------------------------------ |
| "address" | (string, required)             | the address for transactions                                 |
| minconf   | (numeric, optional, default=1) | only include transactions confirmed at least this many times |

### Response

| Name   | Type      | Description                                                  |
| ------ | --------- | ------------------------------------------------------------ |
| amount | (numeric) | the total amount of the relevant coin received at this address |

#### 📌 Examples

Command:

```bash
./komodo-cli getreceivedbyaddress "RJSDZjp7kjBNhHsbECDE1jwYNK7af41pZN"
```

Show Response

```bash
10.0500000
```

Command:

```bash
./komodo-cli getreceivedbyaddress "RJSDZjp7kjBNhHsbECDE1jwYNK7af41pZN" 0
```

Show Response

```bash
10.0500000
```

Command:

```bash
./komodo-cli getreceivedbyaddress "RJSDZjp7kjBNhHsbECDE1jwYNK7af41pZN" 6
```

Show Response

```bash
10.0500000
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "getreceivedbyaddress", "params": ["RJSDZjp7kjBNhHsbECDE1jwYNK7af41pZN", 6] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": 0,
  "error": null,
  "id": "curltest"
}
```