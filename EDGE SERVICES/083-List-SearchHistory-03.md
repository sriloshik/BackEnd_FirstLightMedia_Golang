<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## List Search History - API Specification

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
    <td>23 Sep 2021</td>
    <td>Manikanta Reddy</td>
    <td>Draft Version</td>
  </tr>
  <tr>
    <td>2</td>
    <td>06 Oct 2021</td>
    <td>Yashwanth Lakshmidhar</td>
    <td>Initial Review</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: GET

```
https://<server>/user/search/list
```

#### Request Headers:

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

### Request query params

<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required / Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>pageNumber</td>
    <td>String</td>
    <td>Optional</td>
    <td>Page number</td>
  </tr>
    <tr>
    <td>pageSize</td>
    <td>String</td>
    <td>Optional</td>
    <td>Page size</td>
  </tr>
   <tr>
    <td>sortBy</td>
    <td>String</td>
    <td>Optional</td>
    <td>Sort field</td>
  </tr>
   <tr>
    <td>sortOrder</td>
    <td>String</td>
    <td>Optional</td>
    <td>Sort order. <br/>Allowed values are; asc | desc</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET https://server/user/search/list?pageNumber=1&pageSize=10&sort=ut&order=desc
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
    <td>itemId</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique identifier of item.</td>
  </tr>
  <tr>
    <td>text</td>
    <td>String</td>
    <td>Required</td>
    <td>Search text</td>
  </tr>
  <tr>
    <td>ut</td>
    <td>String</td>
    <td>Required</td>
    <td>Updated time stamp of particular itemId.</td>
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
    "source": "083-03",
    "code": 0,
    "message": "Success",
    "system_time": 1632393117340,
    "start": 1,
    "rows": 3,
    "count": 3,
    "tracking_id": "014b1f5c-e852-45f8-bf63-5235984beb60"
  },
  "data": [
    {
      "itemId": "4113313812",
      "text": "drama332",
      "ut": 1632205468494
    },
    {
      "itemId": "2869110354",
      "text": "comedy",
      "ut": 1631860406544
    },
    {
      "itemId": "4157826037",
      "text": "comedy4343434",
      "ut": 1631514508720
    }
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
    <td>40830301</td>
    <td>Invalid X-Authorization</td>
  </tr>
  <tr>
    <td>40830302</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40830303</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40830304</td>
    <td>Invalid or missing sort by</td>
  </tr>
  <tr>
    <td>40830305</td>
    <td>Invalid or missing sort order</td>
  </tr>
  <tr>
    <td>40830306</td>
    <td>No records found</td>
  </tr>
  <tr>
    <td>40830390</td>
    <td>System failure</td>
  </tr>
  <tr>
    <td>40830391</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to invalid X-Authorization request parameter,

```json
{
  "header": {
    "source": "083-03",
    "code": -1,
    "message": "Failure",
    "system_time": 1632391955826,
    "tracking_id": "62bb75a6-a8ae-484a-af4c-15dc92e7ffb2",
    "errors": [
      {
        "code": "40830301",
        "description": "Invalid X-Authorization"
      }
    ]
  }
}
```

The following response is an example of failure due to invalid page size,

```json
{
  "header": {
    "source": "083-03",
    "code": -1,
    "message": "Failure",
    "system_time": 1632393479524,
    "tracking_id": "25a66010-5dfd-4014-bb5f-d602d725e995",
    "errors": [
      {
        "code": "40830303",
        "description": "Invalid or missing page size"
      }
    ]
  }
}
``` 

The following response is an example of failure due to invalid page number,

```json
{
  "header": {
    "source": "083-03",
    "code": -1,
    "message": "Failure",
    "system_time": 1632393555753,
    "tracking_id": "e052e7e7-9b48-445b-a0e9-2fdf2ff383f7",
    "errors": [
      {
        "code": "40830302",
        "description": "Invalid or missing page number"
      }
    ]
  }
}
``` 

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>