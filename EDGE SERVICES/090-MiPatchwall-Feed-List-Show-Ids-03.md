<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Get Paginated List of Show Ids - API Specification

### Version History

<table width='100%'>
  <tr>
    <th width='20%'>S.No</th>
    <th>Date</th>
    <th>Author</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>1</td>
    <td>22 Sep 2021</td>
    <td>Tulaja Nandewar</td>
    <td>Draft Version</td>
  </tr>
  <tr>
    <td>2</td>
    <td>02 Oct 2021</td>
    <td>Manogar Subramani</td>
    <td>Initial review completed</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: GET

```
https://<server>/content/showidlist
```

#### Request Headers

<table width='100%'>
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>X-Tracking-Id</td>
    <td>String</td>
    <td>Optional</td>
    <td>Unique identifier to trace the HTTP request for errors. The service will auto-generate a new identifier to return in the response if this parameter was not received.<br/>Example - fb8812b9-b5f7-472d-9ab2-8e662253ca03</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Query Parameters

<table width="100%">
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>pageNo</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Number value to indicate the page to retrieve.<br/>
        Example: pageNo=2 indicates second page<br/>
        Default value: 1.
    </td>
  </tr>
   <tr>
    <td>pageSize</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Number value to indicate the number of records to return in response.<br/>
    Example: pageSize=25 indicates to return 25 records per request<br/>
    Default value: 100</td>
  </tr>
   <tr>
    <td>startTime</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Epoch time after which the items are updated</td>
  </tr>
   <tr>
    <td>endTime</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Epoch time before which the items are updated</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET http(s)://server/content/showidlist
GET http(s)://server/content/showidlist?pageNo=2&pageSize=100
GET http(s)://server/content/showidlist?pageNo=5
GET http(s)://server/content/showidlist?pageSize=25
GET http(s)://server/content/showidlist?pageSize=100&pageNo=1&startTime=1630652451&endTime=1630738851
```

### Response

#### Response Headers

<table width="100%">
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Content-Type</td>
    <td>MIME type of the response payload - application/json</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Response Body

<table width="100%">
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>Success or Failure response payload</td>
    <td>JSON</td>
    <td>Required</td>
    <td>Paginated List of id, st(isOnline)</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Response Codes

<table width="100%">
  <tr>
    <th>HTTP Status Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>200</td>
    <td>OK</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example OK Response

The following response is an example of successful list of show records:

```json
{
  "message": "success",
  "code": 0,
  "timestamp": 1631554179,
  "data": {
    "titleIdList": [
      {
        "id": "4ABE8E0C-9A25-4C83-9700-3FA644C041C4",
        "isOnline": false
      },
      {
        "id": "B6602E35-CA45-4B4E-9B5B-9825D90D0198",
        "isOnline": false
      },
      "...": "...",
      "...": "...",
      "...": "..."
    ]
  },
  "pageInfo": {
    "pageCount": 1,
    "hasMore": false,
    "pageSize": 24,
    "pageNo": 1
  }
}
```

### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>1</td>
    <td>Invalid parameters</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Empty data</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Forbidden</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure read due to invalid request parameter:

```json
{
  "message": "failure",
  "code": 1,
  "timestamp": 1631553945
}
```

The following response is an example of failure read due to empty data:

```json
{
  "message": "failure",
  "code": 2,
  "timestamp": 1631553987
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>