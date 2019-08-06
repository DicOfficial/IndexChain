## zcrawjoinsplit

**zcrawjoinsplit rawtx inputs outputs vpub_old vpub_new**

DEPRECATED.

- inputs: a JSON object mapping {note: zcsecretkey, ...}
- outputs: a JSON object mapping {zcaddr: value, ...}

Splices a joinsplit into a raw transaction. Inputs are unilaterally confidential. Outputs are confidential between sender/receiver. The vpub_old and vpub_new values are globally public and move transparent value into or out of the confidential value store, respectively.

Note: The caller is responsible for delivering the output enc1 and enc2 to the appropriate recipients, as well as signing rawtxout and ensuring it is mined. (A future RPC call will deliver the confidential payments in-band on the blockchain.)

Output:

```json
{
  "encryptednote1": enc1,
  "encryptednote2": enc2,
  "rawtxn": rawtxout
}
```