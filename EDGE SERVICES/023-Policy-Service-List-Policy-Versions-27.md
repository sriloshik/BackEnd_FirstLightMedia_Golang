<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## List Policy Versions - API Specification

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
https://<server>/policy/{id}/versions
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
    <td>id</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique identifier of the policy</td>
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
</table>


<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET http(s)://server/policy/a8ae57a5-1d69-4c77-9698-c525fc291446/versions?pageNumber=1&pageSize=10
Authorization: Bearer <Access Token of IAM>
Content-Type: application/json
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
    <td>Get policy versions response</td>
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
    "source": "023-27",
    "code": 0,
    "message": "Success",
    "system_time": 1633269118561,
    "start": 1,
    "rows": 1,
    "count": 1,
    "tracking_id": "4467572a-ee37-42d0-80c4-42510dec2034"
  },
  "data": [
    {
      "id": "e324831b-190b-4144-97e6-2f7ae5702573",
      "key": "e324831b-190b-4144-97e6-2f7ae5702573-1633233378",
      "st": "published"
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
    <td>40232701</td>
    <td>Invalid or missing input policy identifier</td>
  </tr>
  <tr>
    <td>40232702</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40232703</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40232704</td>
    <td>Policy not found</td>
  </tr>
  <tr>
    <td>40232790</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40232791</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Error Samples
The following response is an example of invalid page number:

```` json
{
  "header": {
    "source": "023-27",
    "code": -1,
    "message": "Failure",
    "system_time": 1633269067938,
    "tracking_id": "810611ca-1cee-4c55-960f-e2a4041c82d2",
    "errors": [
      {
        "code": "40232702",
        "description": "Invalid or missing page number"
      }
    ]
  }
}
````

The following response is an example of policy not found:

```` json
{
  "header": {
    "source": "023-27",
    "code": -1,
    "message": "Failure",
    "system_time": 1633268995491,
    "tracking_id": "e019fd55-2065-4162-bb77-771eee5d5586",
    "errors": [
      {
        "code": "40232704",
        "description": "Policy not found"
      }
    ]
  }
}
````

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>
