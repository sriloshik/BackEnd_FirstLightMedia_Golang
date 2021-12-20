<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Consume Policy - API Specification

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
    <td>Suriya Kumar</td>
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
https://<server>/policy/{productName}/{appName}/list
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
    <td>X-Tracking-Id</td>
    <td>String (UUID)</td>
    <td>Optional</td>
    <td>Unique identifier to trace the HTTP request for errors. The service will auto-generate a new identifier to return in the response if this parameter was not received.<br/>Example - fb8812b9-b5f7-472d-9ab2-8e662253ca03</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Path Parameters

<table width='100%'>
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>productName</td>
    <td>String</td>
    <td>Required</td>
    <td>Product Name</td>
  </tr>
 <tr>
    <td>appName</td>
    <td>String</td>
    <td>Required</td>
    <td>Application Name</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Query Parameters

<table width='100%'>
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
    <td>Number value to indicate the page to retrieve.
        <br/>Example: pageNumber=2 indicates second page
        <br/>Default value: 1</td>
  </tr>
 <tr>
    <td>pageSize</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Number value to indicate the number of records to return in response.
        <br/>Example: pageSize=25 indicates to return 25 records per request
        <br/>Default value: 10</td>
  </tr>
  <tr>
    <td>sortBy</td>
    <td>String</td>
    <td>Optional</td>
    <td>Parameter by which the items to be sorted
        <br/>Default value: Updated Time(ut)</td>
  </tr>
  <tr>
    <td>sortOrder</td>
    <td>String</td>
    <td>Optional</td>
    <td>Allowed values: asc or desc</td>
  </tr>
  <tr>
    <td>pty</td>
    <td>String</td>
    <td>Optional</td>
    <td>Policy type Allowed values: application.</td>
  </tr>
</table>


<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request
```json
GET https://server/policy/{productName}/{appName}/list?pty=application&pageNumber=1&pageSize=10
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
    <td>Consume policy response</td>
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

```` json
{
  "header": {
    "source": "023-28",
    "code": 0,
    "message": "Success",
    "system_time": 1633269487767,
    "start": 1,
    "rows": 1,
    "count": 1,
    "tracking_id": "2ef92ada-0e24-48eb-908e-b36596686b42"
  },
  "data": [
    {
      "an": "playback-auth-service",
      "appliesifAll": [
        {
          "aty": "product",
          "n": "reg",
          "op": "oneof",
          "val": [
            "all",
            "us",
            "in",
            "eu",
            "ca",
            "gb",
            "au",
            "my",
            "sg",
            "ae",
            "sa",
            "qa",
            "lk",
            "row",
            "fr",
            "za",
            "mde"
          ]
        }
      ],
      "ct": "2021-10-03T03:56:18Z",
      "ef": [
        {
          "key": "action.allow",
          "type": "Boolean",
          "value": true
        }
      ],
      "id": "e324831b-190b-4144-97e6-2f7ae5702573",
      "key": "e324831b-190b-4144-97e6-2f7ae5702573-1633233378",
      "n": "generic-country-policy",
      "pn": "aha",
      "pty": "application",
      "st": "published",
      "t": "policy",
      "u_id": "manogars",
      "ut": "2021-10-03T12:33:04Z"
    }
  ]
}
````

### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>40232801</td>
    <td>Invalid policy type</td>
  </tr>
  <tr>
    <td>40232802</td>
    <td>Invalid product name</td>
  </tr>
  <tr>
    <td>40232803</td>
    <td>Invalid application name</td>
  </tr>
  <tr>
    <td>40232804</td>
    <td>Invalid lookup reference found in policy</td>
  </tr>
  <tr>
    <td>40232805</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40232806</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40232807</td>
    <td>Invalid or missing sort by</td>
  </tr>
  <tr>
    <td>40232808</td>
    <td>Invalid or missing sort order</td>
  </tr>
  <tr>
    <td>40232809</td>
    <td>Policy not found</td>
  </tr>
  <tr>
    <td>40232890</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40232891</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Error Samples
The following response is an example policy not found:

```` json
{
  "header": {
    "source": "023-28",
    "code": -1,
    "message": "Failure",
    "system_time": 1633269614581,
    "tracking_id": "63836616-af1f-4c16-a8ac-aceae12809cd",
    "errors": [
      {
        "code": "40232809",
        "description": "Policy not found"
      }
    ]
  }
}
````

The following response is an example invalid policy type:

```` json
{
  "header": {
    "source": "023-28",
    "code": -1,
    "message": "Failure",
    "system_time": 1633269593406,
    "tracking_id": "4ffcd74c-f0eb-4ce9-8444-798e508b9cd5",
    "errors": [
      {
        "code": "40232801",
        "description": "Invalid policy type"
      }
    ]
  }
}
````

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>
