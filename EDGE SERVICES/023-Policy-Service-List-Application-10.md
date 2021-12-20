<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## List Application - API Specification

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
https://<server>/policy/urn/resource/product
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
    <td>pageNumber</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Number that indicates the page to retrieve of the paginated list of items. <br>Example: pageNumber=2 indicates second page.<br>Default value: 1.</td>
  </tr>
  <tr>
    <td>pageSize</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Number that indicates the number of records to return in response. <br>Example: pageSize=25 indicates to return 25 records per request. <br>Default value: 10</td>
  </tr>
  <tr>
    <td>sortBy</td>
    <td>String</td>
    <td>Optional</td>
    <td>Field by which the items to be sorted.</td>
  </tr>
  <tr>
    <td>sortOrder</td>
    <td>String</td>
    <td>Optional</td>
    <td>Sort order. ascending (asc) or descending (desc).</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET https://server/policy/urn/resource/application?pageNumber=1&pageSize=10&sortBy=ct&sortOrder=desc
Authorization: Bearer <Access Token of IAM>
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
    <td>List application response</td>
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
    "source": "023-10",
    "code": 0,
    "message": "Success",
    "system_time": 1633107271122,
    "start": 1,
    "rows": 7,
    "count": 7,
    "tracking_id": "07c7f6ef-109b-49e4-86c2-a07b27f95a65"
  },
  "data": [
    {
      "ct": "2021-10-01T16:41:00Z",
      "id": "09D74CAB-EC07-4D50-81FB-67FCE49D663C",
      "n": "Aha-1",
      "t": "application",
      "u_id": "testproject_admin",
      "ut": "2021-10-01T16:46:59Z"
    },
    {
      "ct": "2021-10-01T16:37:39Z",
      "id": "49A6403A-DC27-46BD-98D4-780BE4D1141D",
      "n": "aha-1",
      "t": "application",
      "u_id": "testproject_admin",
      "ut": "2021-10-01T16:37:39Z"
    },
    {
      "ct": "2021-08-06T06:50:57Z",
      "desc": "Application Description",
      "id": "C11A3324-1366-454F-9A23-3C932C523AFD",
      "n": "application-10",
      "t": "application",
      "u_id": "sreekantak",
      "ut": "2021-08-06T06:50:57Z"
    },
    "...": "...",
    "...": "...",
    "...": "..."
  ]
}
```

### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>40231001</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40231002</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40231003</td>
    <td>Invalid or missing sort by</td>
  </tr>
  <tr>
    <td>40231004</td>
    <td>Invalid or missing sort order</td>
  </tr>
   <tr>
    <td>40231005</td>
    <td>Item not found</td>
  </tr>
  <tr>
    <td>40231090</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40231091</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to item not found:
```json
{
  "header": {
    "source": "023-10",
    "code": -1,
    "message": "Failure",
    "system_time": 1633108798266,
    "tracking_id": "1dfb4dbe-dd8a-4172-bbb5-ccbdaefdd5aa",
    "errors": [
      {
        "code": "40231005",
        "description": "Item not found"
      }
    ]
  }
}
```

The following response is an example of failure due to invalid or missing page number:
```json
{
  "header": {
    "source": "023-10",
    "code": -1,
    "message": "Failure",
    "system_time": 1633108200037,
    "tracking_id": "2b02c668-6d18-4acf-8e9b-cbe3a0e69c79",
    "errors": [
      {
        "code": "40231001",
        "description": "Invalid or missing page number"
      }
    ]
  }
}
```
The following response is an example of failure due to invalid or missing page size:

```json
{
  "header": {
    "source": "023-10",
    "code": -1,
    "message": "Failure",
    "system_time": 1633108416759,
    "tracking_id": "64e309e9-fdcb-4062-9e62-72bbf233f0ea",
    "errors": [
      {
        "code": "40231002",
        "description": "Invalid or missing page size"
      }
    ]
  }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>