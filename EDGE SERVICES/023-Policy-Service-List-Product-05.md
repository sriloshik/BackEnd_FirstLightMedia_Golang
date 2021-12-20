<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## List Product - API Specification

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
    <td>Number that indicates the number of records to return in response. <br>Example: pageSize=25 indicates to return 25 records per request. <br>Default value:10</td>
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
    <td>Sort order; ascending (asc) or descending (desc).</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET https://server/policy/urn/resource/product?pageNumber=1&pageSize=10&sortBy=ct&sortOrder=desc
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
    <td>List product response</td>
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
    "source": "023-05",
    "code": 0,
    "message": "Success",
    "system_time": 1633105203635,
    "start": 1,
    "rows": 2,
    "count": 2,
    "tracking_id": "1d272d3f-a2cc-4bf6-b685-742c5487e750"
  },
  "data": [
    {
      "ct": "2021-10-01T16:07:37Z",
      "id": "732915C9-5156-45D3-A5BF-A67EFAA8C9DA",
      "n": "aha-1",
      "t": "product",
      "u_id": "testproject_admin",
      "ut": "2021-10-01T16:07:37Z"
    },
    {
      "ct": "2021-07-28T08:58:33Z",
      "id": "EDC0215D-8B35-4C8D-AEC3-815250F6CF12",
      "n": "aha",
      "t": "product",
      "u_id": "fldemo_admin",
      "ut": "2021-07-28T08:58:33Z"
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
    <td>40230501</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40230502</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40230503</td>
    <td>Invalid or missing sort by</td>
  </tr>
  <tr>
    <td>40230504</td>
    <td>Invalid or missing sort order</td>
  </tr>
   <tr>
    <td>40230505</td>
    <td>Item not found</td>
  </tr>
  <tr>
    <td>40230590</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40230591</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to item not found:

```json
{
  "header": {
    "source": "023-05",
    "code": -1,
    "message": "Failure",
    "system_time": 1633108798266,
    "tracking_id": "1dfb4dbe-dd8a-4172-bbb5-ccbdaefdd5aa",
    "errors": [
      {
        "code": "40230505",
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
    "source": "023-05",
    "code": -1,
    "message": "Failure",
    "system_time": 1633108984153,
    "tracking_id": "9dc9fe1e-3c8d-4327-90b2-0a8d66efc275",
    "errors": [
      {
        "code": "40230501",
        "description": "Invalid or missing page number"
      }
    ]
  }
}
```

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>