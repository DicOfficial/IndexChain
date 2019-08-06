## sendtoaddress

**sendtoaddress "address" amount ( "comment" "comment-to" subtractfeefromamount )**

The `sendtoaddress` method sends an amount to a given address. The amount is real and is rounded to the nearest 0.00000001.

### Arguments

| Name                  | Type                               | Description                                                  |
| --------------------- | ---------------------------------- | ------------------------------------------------------------ |
| "komodoaddress"       | (string, required)                 | the receiving address                                        |
| "amount"              | (numeric, required)                | the amount to send (json requires all decimals values less than 1 begin with the characters '0.') |
| "comment"             | (string, optional)                 | a comment used to store what the transaction is for; this is not part of the transaction, just kept in your wallet |
| "comment-to"          | (string, optional)                 | a comment to store the name of the person or organization to which you're sending the transaction; this is stored in your local wallet file only |
| subtractfeefromamount | (boolean, optional, default=false) | when `true`, the fee will be deducted from the amount being sent |

### Response

| Name             | Type     | Description        |
| ---------------- | -------- | ------------------ |
| "transaction_id" | (string) | the transaction id |

#### 📌 Examples

Command:

```bash
./komodo-cli sendtoaddress "RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ" 0.1
```

Show Response

```bash
cc23924c007adc98b8ea5b9b8b47638e080aa469eb9738b976def487a44f467b
```

Command:

```bash
./komodo-cli sendtoaddress "RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ" 0.1 "donation" "seans outpost"
```

Show Response

```bash
86948c27dc63be415b235c5b3ed807c1e07d9a2cac252f58734add700c55fe18
```

Command:

```bash
./komodo-cli sendtoaddress "RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ" 0.1 "" "" true
```

Show Response

```bash
c5727cafd7d6dfc888d4a0596dc58bfafb24859e29f827e1bf1443037d8461fc
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "sendtoaddress", "params": ["RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ", 0.1, "donation", "seans outpost"] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": "6e411f3534af8847d705d87934f6061046e2034abad96b7a1fb1d3996129cb1e",
  "error": null,
  "id": "curltest"
}
```