## signmessage

**signmessage "address" "message"**

The `signmessage` method signs a message via the private key of an address.

### Arguments

| Name      | Type               | Description                            |
| --------- | ------------------ | -------------------------------------- |
| "address" | (string, required) | the address to use for the private key |
| "message" | (string, required) | the message                            |

### Response

| Name        | Type     | Description                                     |
| ----------- | -------- | ----------------------------------------------- |
| "signature" | (string) | the signature of the message encoded in base 64 |

#### 📌 Examples

Create the signature:

Command:

```bash
./komodo-cli signmessage "RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ" "my message"
```

Show Response

```bash
H1y0mn/wRv56r1bcfkbQtzjG6XeWSelAsyayBuCwEL9XGXs7ieU55dryt/cFWM9gnRFI7gS01AByuSqRs+o/AZs=
```

Verify the signature:

Command:

```bash
./komodo-cli verifymessage "RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ" "H1y0mn/wRv56r1bcfkbQtzjG6XeWSelAsyayBuCwEL9XGXs7ieU55dryt/cFWM9gnRFI7gS01AByuSqRs+o/AZs=" "my message"
```

Show Response

```bash
true
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "signmessage", "params": ["RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ", "my message"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "H1y0mn/wRv56r1bcfkbQtzjG6XeWSelAsyayBuCwEL9XGXs7ieU55dryt/cFWM9gnRFI7gS01AByuSqRs+o/AZs=",
  "error": null,
  "id": "curltest"
}
```