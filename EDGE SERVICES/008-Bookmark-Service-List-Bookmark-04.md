<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Continue Watching - Listings - API Specification

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
  <tr>
    <td>3</td>
    <td>05 Oct 2021</td>
    <td>Senthilkumar Jeyarajan</td>
    <td>Reviewed and Published</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: GET

```
https://<server>/user/bookmark/list
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
    <td>Authorization</td>
    <td>String</td>
    <td>Required</td>
    <td>Bearer &lt;Access Token of <b>IAM</b>&gt;</td>
  </tr>
  <tr>
    <td>X-Authorization</td>
    <td>String</td>
    <td>Required</td>
    <td>Access Token of <b>User Management System</b> to identify the user.</td>
  </tr>
  <tr>
    <td>X-Tracking-Id</td>
    <td>String</td>
    <td>Optional</td>
    <td>Unique identifier to trace the HTTP request for errors. The service will auto-generate a new identifier to return in the response if this parameter was not received.<br/>Example - fb8812b9-b5f7-472d-9ab2-8e662253ca03</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Query Parameters

<table width="100%">
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required / Optional</th>
    <th>Description</th>
  </tr>
   <tr>
    <td>pageNumber</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Number that indicates the page to retrieve of the paginated list of items. <br>Example: pageNumber=2 indicates second page.<br>Default value: 1.</td>
  </tr>
  <tr>
    <td>pageSize</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Number that indicates the number of records to return in response. <br>Example: pageSize=25 indicates to return 25 records per request. <br>Default value: 100.</td>
  </tr>
  <tr>
    <td>sort</td>
    <td>String</td>
    <td>Optional</td>
    <td>Field by which the items to be sorted. <br>Default value: timestamp.</td>
  </tr>
  <tr>
    <td>order</td>
    <td>String</td>
    <td>Optional</td>
    <td>Sort order. ascending (asc) or descending (desc).</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">


#### Example Request

```json
GET http(s)://server/user/bookmark/list
Authorization: Bearer <Access Token of IAM>
X-Authorization: Access Token of User Management System to identify the user.
```

```json
GET http(s)://server/user/bookmark/list?pageNumber=2&pageSize=100
Authorization: Bearer <Access Token of IAM>
X-Authorization: Access Token of User Management System to identify the user.
```

```json
GET http(s)://server/user/bookmark/list?pageNumber=5
Authorization: Bearer <Access Token of IAM>
X-Authorization: Access Token of User Management System to identify the user.
```

```json
GET http(s)://server/user/bookmark/list?pageSize=25
Authorization: Bearer <Access Token of IAM>
X-Authorization: Access Token of User Management System to identify the user.
```

<div class="page"/>

```json
GET http(s)://server/user/bookmark/list?sort=timestamp&order=asc
Authorization: Bearer <Access Token of IAM>
X-Authorization: Access Token of User Management System to identify the user.
```

```json
GET http(s)://server/user/bookmark/list?pageNumber=2&pageSize=25&sort=timestamp&order=asc
Authorization: Bearer <Access Token of IAM>
X-Authorization: Access Token of User Management System to identify the user.
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
    <td>JSON payload</td>
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
  <tr>
    <td>400</td>
    <td>Bad Request</td>
  </tr>
  <tr>
    <td>401</td>
    <td>Unauthorized</td>
  </tr>
  <tr>
    <td>403</td>
    <td>Forbidden</td>
  </tr>
  <tr>
    <td>500</td>
    <td>Internal Server Error</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example OK Response

```json
{
  "header": {
    "source": "008-04",
    "code": 0,
    "message": "Success",
    "system_time": 1633093743983,
    "start": 1,
    "rows": 10,
    "count": 10,
    "tracking_id": "4b6ea897-b2ba-4884-957c-f6716e5f80c3"
  },
  "data": [
    {
      "itemId": "content123",
      "offset": 100,
      "ut": 1633092707736
    },
    {
      "itemId": "content456",
      "offset": 100,
      "ut": 1632330258453
    },
    {
      "episodeId": "episode36",
      "itemId": "itemid-36",
      "offset": 120,
      "seasonId": "season36",
      "ut": 1631686767623
    },
    "...": "...",
    "...": "...",
    "...": "..."
  ]
}
```

<div class="page"/>

### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>40080401</td>
    <td>Invalid X-Authorization</td>
  </tr>
  <tr>
    <td>40080402</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40080403</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40080404</td>
    <td>Invalid or missing sort by</td>
  </tr>
  <tr>
    <td>40080405</td>
    <td>Invalid or missing sort order</td>
  </tr>
   <tr>
    <td>40080406</td>
    <td>Item not found / No record found</td>
  </tr>
  <tr>
    <td>40080490</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40080491</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to invalid X-Authorization request parameter:

```json
{
  "header": {
    "source": "008-04",
    "code": -1,
    "message": "Failure",
    "system_time": 1632117106200,
    "tracking_id": "0af5cba7-7dd7-4f6f-8ddf-f55524b48b3b",
    "errors": [
      {
        "code": "40080401",
        "description": "Invalid X-Authorization"
      }
    ]
  }
}
```

<div class="page"/>

The following response is an example of failure due to Invalid or missing page number:

```json
{
  "header": {
    "source": "008-04",
    "code": -1,
    "message": "Failure",
    "system_time": 1632118510501,
    "tracking_id": "eabbfb72-46c6-4c4e-a97a-718db486fab9",
    "errors": [
      {
        "code": "40080402",
        "description": "Invalid or missing page number"
      }
    ]
  }
}
```


The following response is an example of failure due to Invalid or missing page size:

```json
{
  "header": {
    "source": "008-04",
    "code": -1,
    "message": "Failure",
    "system_time": 1632118750088,
    "tracking_id": "c3d5bea6-7392-4b23-8007-7ef16de283ee",
    "errors": [
      {
        "code": "40080403",
        "description": "Invalid or missing page size"
      }
    ]
  }
}
```

<div class="page"/>

The following response is an example of no items found for the request:

```json
{
  "header": {
    "source": "001-04",
    "code": "-1",
    "message": "Failure",
    "system_time": 1558041284123,
    "tracking_id": "fb8812b9-b5f7-472d-9ab2-8e662253ca03",
    "errors": [
      {
        "code": "40010406",
        "description": "No records found"
      }
    ]
  }
}
```

<br/>

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>