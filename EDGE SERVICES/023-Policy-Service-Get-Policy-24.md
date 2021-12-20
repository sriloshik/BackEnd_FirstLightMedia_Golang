<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Get Policy - API Specification

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
https://<server>/policy/urn/resource/rule/{id}
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
    <td>Unique identifier of the Policy</td>
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
    <td>st</td>
    <td>String</td>
    <td>Optional</td>
    <td>Policy status. Allowed values: published, draft, purged, archived.</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET http(s)://server/policy/urn/resource/rule/2162BC93-B26D-4E46-AD1D-2B66EE36B18F?st=published
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
    <td>Get policy response</td>
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
    "source": "023-24",
    "code": 0,
    "message": "Success",
    "system_time": 1633266486849,
    "tracking_id": "e269682b-fe25-457f-b056-39483a4dc420"
  },
  "data": {
    "an": "playback-auth-service",
    "appliesifAll": [
      {
        "aty": "product",
        "n": "reg",
        "op": "oneof",
        "val": "reg"
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
}
````
### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>40232401</td>
    <td>Invalid or missing policy identifier</td>
  </tr>
  <tr>
    <td>40232402</td>
    <td>Invalid or missing status</td>
  </tr>
  <tr>
    <td>40232403</td>
    <td>Policy not found</td>
  </tr>
  <tr>
    <td>40232490</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40232491</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Error Samples
The following response is an example of policy not found:

```` json
{
  "header": {
    "source": "023-24",
    "code": -1,
    "message": "Failure",
    "system_time": 1633266640256,
    "tracking_id": "2b3eef81-c48b-4a29-9c92-30aad631a4df",
    "errors": [
      {
        "code": "40232403",
        "description": "Policy not found"
      }
    ]
  }
}
````

The following response is an example of invalid or missing status:

```` json
{
  "header": {
    "source": "023-24",
    "code": -1,
    "message": "Failure",
    "system_time": 1633266661171,
    "tracking_id": "ad68a2f0-48e0-40e7-917f-4a1f59f116e0",
    "errors": [
      {
        "code": "40232402",
        "description": "Invalid or missing status"
      }
    ]
  }
}
````
<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>
