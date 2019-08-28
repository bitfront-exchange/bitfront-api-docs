# Coin transfer history

Retrieves your coin transfer history under the given conditions. <br/>
You can set the conditions through the query parameters. See the parameter descriptions. <br/>
`responseData.content` in the response will pass the result data, which are sorted in descending order of `responseData.content.date`.

## Endpoint URI

```
GET https://openapi.bitbox.me/v1/account/transactionHistory?currency={currency}&startTime={startTime}&endTime={endTime}&transferType={transferType}&page={page}&pageSize={pageSize}
```

## Request parameters

| Name                               | Description                                                                 | Type  | Loc.  | Required |
| ---------------------------------- | --------------------------------------------------------------------------- | ----- | ----- | -------- |
| `currency`                         | A string literal for the [Currency](/5_Terms.md#currency-for-coin-trading). <br/>For example, BCH for Bitcoin Cash. | String | query |       |
| `startTime`                        | The earliest time of trades to retrieve. It is in milliseconds in UTC.      | Long  | query |          |
| `endTime`                          | The latest time of trades to retrieve. It is in milliseconds in UTC.        | Long  | query |          |
| `transferType`                     | The type of transfer. It should be empty or one of the following: <br/>- "WITHDRAW": retrieves the withdrawal records only. <br/>- "DEPOSIT": retrieve the deposit records only. <br/>Omit it to retrieve both types of transfer. <br/>Note that this parameter is not case sensitive. | String | query | |
| `page` | The page number to retrieve. <br/>The number starts at 0, and the default is 0. | Integer | query | |
| `pageSize` | The number of records each page will display. The default is 20, and maximum is 1000. <br/>- If `page` is 0 and `pageSize` is 20, then this API will return 1st-20th records. <br/>- If `page` is 1 and `pageSize` is 20, then this API will return 21th-40th records. | Integer | query | |

## Response

| Name                                                       | Description                                                                                                | Type                          | Included |
| ---------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ----------------------------- | -------- |
| `timezone`     | The time standard for the `responseTime`. It is always "UTC". | String | O        |
| `responseTime` | The time when responded. <br/>It is a timestamp in milliseconds since Unix Epoch in UTC. | Long | O                             |
| `statusCode`   | The result status code. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | Integer                       | O        |
| `statusMessage`| The detailed message of the result. See [`statusCode` definitions](/1_Overview.md#statuscode-definitions). | String | O        |
| `responseData` | See the reference object. | [responseData](#responsedata) |          |

### responseData

- Type: object

| Name               | Description                                        | Type                | Included |
| ------------------ | -------------------------------------------------- | ------------------- | -------- |
| `number`           | The page number                                    | Integer             |          |
| `size`             | The size of the page                               | Integer             |          |
| `totalPages`       | The number of pages                                | String              |          |
| `numberOfElements` | The number of elements in the page                 | Integer             |          |
| `totalElements`    | The number of elements returned                    | Integer             |          |
| `previousPage`     | The flag indicating whether it has a previous page | Boolean             |          |
| `first`            | The flag indicating whether it is the first page   | Boolean             |          |
| `nextPage`         | The flag indicating whether it has a next page     | Boolean             |          |
| `last`             | The flag indicating whether it is the last page    | Boolean             |          |
| `content`          | . See the reference object.                        | [content](#content) |          |

### content

- Type: object

| Name           | Description                                                                               | Type   | Included |
| -------------- | ----------------------------------------------------------------------------------------- | ------ | -------- |
| `date`         | The time of the coin transfer. It is a timestamp in milliseconds since Unix Epoch in UTC. | Long   |          |
| `coinType`     | A [coin code](/5_Terms.md#coin-code) of the transferred coin                              | String |          |
| `transferType` | The type of the coin transfer. It is one of the following: <br/>- "WITHDRAW": Withdrawal transfer <br/>- "DEPOSIT": Deposit transfer | String | |
| `amount` | The amount of the coin to transfer | Double | |
| `fee` | The transfer fee | Double | |
| `total` | `amount + fee` | Double | |
| `address` | The target address | String | |
| `status` | The status of the coin transfer. It should be one of the following: <br/>- "REQUEST": The transfer is requested. <br/>- "PENDING": The transfer is pending. <br/>- "CONFIRM": The transfer is confirmed. <br/>- "FAIL": The transfer fails. <br/>- "CANCEL_REQUEST": The transfer is requested for cancellation. <br/>- "CANCEL": The transfer is completely cancelled. <br/>- "CANCEL_FAIL": The transfer is requested for cancellation but the cancellation fails. | String | |

**A response example**

```json
{
  "timezone": "UTC",
  "responseTime": 1527658634583,
  "statusCode": 1000,
  "statusMessage": "SUCCESS",
  "responseData": {
    "number": 0,
    "size": 100,
    "totalPages": 1,
    "numberOfElements": 2,
    "totalElements": 2,
    "previousPage": false,
    "first": true,
    "nextPage": false,
    "last": true,
    "content": [
      {
        "date": 1525420991000,
        "coinType": "BTC",
        "transferType": "WITHDRAW",
        "amount": 0.5,
        "fee": 0,
        "total": 0.5,
        "address": "2N8V9g4Ezd5wFGmoNgJYy8YUuYUMYqnATWJ",
        "status": "CONFIRM"
      },
      {
        "date": 1525420983000,
        "coinType": "BTC",
        "transferType": "WITHDRAW",
        "amount": 0.5,
        "fee": 0,
        "total": 0.5,
        "address": "2N9rMM6SrSZ7Xspfqu1QMmTXVvYGm8KPjTu",
        "status": "CONFIRM"
      }
    ]
  }
}
```
