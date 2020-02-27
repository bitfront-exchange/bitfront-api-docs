# Currency balance

Gets your account currency balance for the given currency.

## Endpoint URI

```
GET https://openapi.bitfront.me/v1/account/balances/{currency}
```

## Request parameters

| Name                               | Description                                                                                      | Type | Loc. | Required |
| ---------------------------------- | ------------------------------------------------------------------------------------------------ | ---- | ---- | -------- |
| `currency`                         | A [coin code](/5_Terms.md#coin-code) of the [Currency](/5_Terms.md#currency-for-coin-trading). <br/>For example, BCH for Bitcoin Cash. | String | path | O    |

## Response

| Name                                                       | Description                                                                                                | Type                          | Included |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ----------------------------- | -------- |
| `timezone`                                                 | The time standard for the `responseTime`. It is always "UTC".                                              | String                        | O        |
| `responseTime`                                             | The time when responded. <br/>It is a timestamp in milliseconds since Unix Epoch in UTC. | Long | O                             |
| `statusCode`                                               | The result status code. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions).             | Integer                       | O        |
| `statusMessage`                                            | The detailed message of the result. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | String                        | O        |
| `responseData`                                             | See the reference object. | [responseData](#responsedata) |          |

### responseData

- Type: object

| Name | Description | Type | Included |
|---|---|---|---|
| `currency`|A [coin code](/5_Terms.md#coin-code) of the [Currency](/5_Terms.md#currency-for-coin-trading)|String||
| `balance`|The total cryptocurrency balance|Double||
| `availableBalance`|The total cryptocurrency balance that can be used (unlocked)|Double||

**A response example**

```json
{
  "timezone": "UTC",
  "responseTime": 1525239832135,
  "statusCode": 1000,
  "statusMessage": "SUCCESS",
  "responseData": [
    {
      "currency": "ETH",
      "balance": 1000107794.9999858,
      "availableBalance": 1000107794.9999858
    }
  ]
}
```
