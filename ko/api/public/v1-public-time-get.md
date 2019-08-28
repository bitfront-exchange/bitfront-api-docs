# Server time

서버의 현재 시각을 가져옵니다. 반환값은 밀리초 단위 Unix Epoch (UTC)의 타임스탬프입니다.

> **Note**
>
> 이 API는 헤더 파라미터에 `X-API-Key`만 전달하면 됩니다.

## Endpoint URI

```
GET https://openapi.bitbox.me/v1/public/time
```

## Request parameters

None

## Response

| Name           | Description                                | Type   | Included |
| -------------- | ------------------------------------------ | ------ | -------- |
| `timezone`     | `responseTime`의 기준 시간. 항상 “UTC”.           | String | O        |
| `responseTime` | 응답 시간. 밀리초 단위의 Unix Epoch in UTC 타임스탬프입니다. | Long   | O        |

**A response example**

``` json
{
  "timezone": "UTC",
  "responseTime": 1527747579424
}
```
