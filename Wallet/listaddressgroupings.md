## listaddressgroupings

**listaddressgroupings**

The `listaddressgroupings` method lists groups of addresses which have had their common ownership made public by common use as inputs or as the resulting change in past transactions.

### Arguments

| Name   | Type | Description |
| ------ | ---- | ----------- |
| (none) |      |             |

### Response

| Name       | Type               | Description              |
| ---------- | ------------------ | ------------------------ |
| "address", | (string)           | the address              |
| amount,    | (numeric)          | the amount               |
| "account"  | (string, optional) | (DEPRECATED) the account |

#### 📌 Examples

Command:

```bash
./komodo-cli listaddressgroupings
```

Show Response

(note how there are two separate, unique groupings of addresses)

```bash
[
  [
    [
      "RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ",
      9.99304496
    ],
    [
      "RDNC9mLrN48pVGDQ5jSoPb2nRsUPJ5t2R7",
      0.00040000,
      ""
    ],
    [
      "RJSDZjp7kjBNhHsbECDE1jwYNK7af41pZN",
      0.01000000
    ]
  ],
  [
    [
      "RTcwYaQPDVN7V9SdfFHARWnoB7vcpSfdvs",
      0.00990000,
      ""
    ]
  ]
]
```

You can find your `rpcuser`, `rpcpassword`, and `rpcport` in the coin's `.conf` file.

Command:

```bash
curl --user myrpcuser:myrpcpassword --data-binary '{"jsonrpc": "1.0", "id":"curltest", "method": "listaddressgroupings", "params": [] }' -H 'content-type: text/plain;' http://127.0.0.1:myrpcport/
```

Show Response

```json
{
  "result": [
    [
      ["RBtNBJjWKVKPFG4To5Yce9TWWmc2AenzfZ", 9.99304496],
      ["RDNC9mLrN48pVGDQ5jSoPb2nRsUPJ5t2R7", 0.0004, ""],
      ["RJSDZjp7kjBNhHsbECDE1jwYNK7af41pZN", 0.01]
    ],
    [["RTcwYaQPDVN7V9SdfFHARWnoB7vcpSfdvs", 0.0099, ""]]
  ],
  "error": null,
  "id": "curltest"
}
```