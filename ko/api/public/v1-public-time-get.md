# Server time

서버의 현재 시각을 가져옵니다. 반환값은 밀리초 단위 Unix Epoch (UTC)의 타임스탬프입니다.<br/>

> **Note**<br/>
> 이 API는 헤더 파라미터에 `X-API-Key`만 전달하면 됩니다.

## Endpoint URI

    GET https://openapi.bitbox.me/v1/public/time

## Request parameters

None

## Response

<table>

<colgroup>

<col style="width: 12%">

<col style="width: 56%">

<col style="width: 12%">

<col style="width: 10%">

<col style="width: 10%">

</colgroup>

<thead>

<tr class="header">

<th>

<strong>Name</strong>

</th>

<th>

<strong>Description</strong>

</th>

<th style="text-align: center;">

<strong>Type</strong>

</th>

<th style="text-align: center;">

<strong>Included</strong>

</th>

</tr>

</thead>

<tbody>

<tr>

<td>

`timezone`

</td>

<td>

`responseTime`의 기준 시간. 항상 "UTC".

</td>

<td style="text-align: center;">

String

</td>

<td style="text-align: center;">

O

</td>

</tr>

<tr>

<td>

`responseTime`

</td>

<td>

응답 시간. 밀리초 단위의 Unix Epoch in UTC 타임스탬프입니다.

</td>

<td style="text-align: center;">

Long

</td>

<td style="text-align: center;">

O

</td>

</tr>

</tbody>

</table>

**A response example**

``` json
{
  "timezone": "UTC",
  "responseTime": 1527747579424
}
```

<p/>
