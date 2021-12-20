<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## List Storefront - API Specification

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
https://<server>/storefront/list
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
    <td>pageNumber</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Number that indicates the page to retrieve of the paginated list of items. <br>Example: pageNumber=2 indicates second page.<br>Default value: 1</td>
  </tr>
  <tr>
    <td>pageSize</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Number that indicates the number of records to return in response. <br>Example: pageSize=25 indicates to return 25 records per request.<br>Default value: 10</td>
  </tr>
  <tr>
    <td>ty</td>
    <td>String</td>
    <td>Optional</td>
    <td>Type of storefront.<br>Default value: <b>Collection</b> when ids parameter is sent in request, <b>Storefront</b> otherwise</td>
  </tr>
  <tr>
    <td>ids</td>
    <td>String</td>
    <td>Optional</td>
    <td>List of collection ids</td>
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

#### Example Request

```json
GET https://server/storefront/list??pageNumber=1&pageSize=100&ty=Storefront&st=published&sortOrder=asc
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
    <td>List storefront response</td>
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
    "source": "087-01",
    "code": 0,
    "message": "Success",
    "system_time": 1633096582402,
    "start": 1,
    "rows": 1,
    "count": 1,
    "tracking_id": "e889d275-a635-4699-ae8c-9b1e0bf059ea"
  },
  "data": [
    {
      "appliesif": {
        "acl": [
          "te"
        ],
        "dt": [
          "all"
        ],
        "reg": [
          "all"
        ],
        "sp": [
          "urn:package:te-monthly",
          "urn:package:te-quarterly",
          "urn:package:te-annual",
          "urn:package:combo",
          "urn:package:free"
        ]
      },
      "bgc": "#000000",
      "ct": "2021-09-30T01:59:18Z",
      "ed_dt": "2025-05-25T18:29:00.000Z",
      "id": "BCF5C97B-6E05-4891-AD4C-4F87FA39BD63",
      "key": "BCF5C97B-6E05-4891-AD4C-4F87FA39BD63-1632967138",
      "...": "..."
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
    <td>40870101</td>
    <td>Item not found</td>
  </tr>
  <tr>
    <td>40870102</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40870103</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40870104</td>
    <td>Invalid sort order</td>
  </tr>
  <tr>
    <td>40870105</td>
    <td>Invalid or missing policy attribute</td>
  </tr>
  <tr>
    <td>40870190</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40870191</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to storefront or collections not found:

```json
{
  "header": {
    "source": "087-01",
    "code": -1,
    "message": "Failure",
    "system_time": 1632216777337,
    "tracking_id": "93ee8ccb-dd52-4137-ae08-96337408ad2b",
    "errors": [
      {
        "code": "40870101",
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
    "source": "087-01",
    "code": -1,
    "message": "Failure",
    "system_time": 1633097022613,
    "tracking_id": "170cf96e-b96e-480d-b381-170ab202ab55",
    "errors": [
      {
        "code": "40870102",
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
    "source": "087-01",
    "code": -1,
    "message": "Failure",
    "system_time": 1632216428366,
    "tracking_id": "fbf61c54-d435-43b3-b144-406917b45161",
    "errors": [
      {
        "code": "40870103",
        "description": "Invalid or missing page size"
      }
    ]
  }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>