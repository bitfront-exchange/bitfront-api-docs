# Server time

Gets the server's current time in milliseconds since Unix Epoch in UTC.<br/>
<br/>

> **Note**<br/>
> Only `X-API-Key` is required in the request header for this API.

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

The time standard for the `responseTime`. It is always "UTC".

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

The time when it responds.<br/>
It is a timestamp in milliseconds since Unix Epoch in UTC.

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
