# Server time

Gets the server's current time in milliseconds since Unix Epoch in UTC.

> **Note**
>
> This API can be used without API KEY.

## Endpoint URI

```
GET https://openapi.bitfront.me/v1/public/time
```

## Request parameters

None

## Response

| Name           | Description                                                   | Type   | Included |
| -------------- | ------------------------------------------------------------- | ------ | -------- |
| `timezone`     | The time standard for the `responseTime`. It is always "UTC". | String | O        |
| `responseTime` | The time when it responds. <br/>It is a timestamp in milliseconds since Unix Epoch in UTC. | Long | √ |

**A response example**

``` json
{
  "timezone": "UTC",
  "responseTime": 1527747579424
}
```
