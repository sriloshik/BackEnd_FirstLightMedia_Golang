<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Update Policy - API Specification

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

#### HTTP Method: PUT

```
https://<server>/policy/urn/resource/rule/{key}
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
    <td>key</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique identifier of Version</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Request Body

<table width='100%'>
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>n</td>
    <td>String</td>
    <td>Required</td>
    <td>Policy Name</td>
  </tr>
  <tr>
    <td>t</td>
    <td>String</td>
    <td>Required</td>
    <td>Resource Type. Allowed values: policy</td>
  </tr>
  <tr>
    <td>pty</td>
    <td>String</td>
    <td>Required</td>
    <td>Policy Type. Allowed values: application</td>
  </tr>
  <tr>
    <td>pn</td>
    <td>String</td>
    <td>Required</td>
    <td>Product Name</td>
  </tr>
  <tr>
    <td>an</td>
    <td>String</td>
    <td>Required</td>
    <td>Application Name</td>
  </tr>
  <tr>
    <td>id</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique Identifier of Resource</td>
  </tr>  
  <tr>
    <td>key</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique identifier of Version</td>
  </tr>
  <tr>
    <td>appliesifAll</td>
    <td>Condition Object Array</td>
    <td>Optional</td>
    <td>Match all conditions
        <br/>Policy will be applied only if all of the conditions are satisfied
        <br/>See JSON Schema for the Condition Object stricture</td>
  </tr>
  <tr>
    <td>appliesifAny</td>
    <td>Condition Object Array</td>
    <td>Optional</td>
    <td>Match any conditions
        <br/>Policy will be applied if any one or more of the conditions are satisfied</td>
  </tr>
  <tr>
    <td>desc</td>
    <td>String</td>
    <td>Optional</td>
    <td>Policy Description</td>
  </tr>
  <tr>
    <td>st</td>
    <td>String</td>
    <td>Optional</td>
    <td>Publication Status
        <br/>Allowed values : published, draft, archived</td>
  </tr>
</table>


<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
PUT http(s)://server/policy/urn/resource/rule/a8ae57a5-1d69-4c77-9698-c525fc291445-1623062570
Authorization: Bearer <Access Token of IAM>
Content-Type: application/json

{
  "an": "playback-auth-servicea",
  "appliesifAll": [
    {
      "aty": "product",
      "n": "a",
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
  "ut": "2021-10-03T03:56:18Z"
}
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
    <td>Update policy response</td>
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
    "source": "023-23",
    "code": 0,
    "message": "Success",
    "system_time": 1633264384320,
    "tracking_id": "395c296c-6280-4dff-86c4-a3b319a5f072"
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
    <td>40232301</td>
    <td>Invalid Authorization</td>
  </tr>
  <tr>
    <td>40232302</td>
    <td>Invalid or missing policy identifier</td>
  </tr>
  <tr>
    <td>40232303</td>
    <td>Policy not found</td>
  </tr>
  <tr>
    <td>40232304</td>
    <td>Active draft content already exists</td>
  </tr>
  <tr>
    <td>40232305</td>
    <td>Invalid status</td>
  </tr>
  <tr>
    <td>40232306</td>
    <td>Invalid product</td>
  </tr>
  <tr>
    <td>40232307</td>
    <td>Invalid application</td>
  </tr>
  <tr>
    <td>40232308</td>
    <td>Invalid attribute</td>
  </tr>
  <tr>
    <td>40232309</td>
    <td>Invalid lookup</td>
  </tr>
  <tr>
    <td>40232310</td>
    <td>Invalid status update</td>
  </tr>
  <tr>
    <td>40232390</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40232391</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Error Samples
The following response is an example of failure due to invalid attribute:

```` json
{
  "header": {
    "source": "023-23",
    "code": -1,
    "message": "Failure",
    "system_time": 1633265095880,
    "tracking_id": "a19c6a4b-9284-4152-b468-7dc6a2c058d6",
    "errors": [
      {
        "code": "40232308",
        "description": "Invalid attribute"
      }
    ]
  }
}
````

The following response is an example of failure due to invalid application name:

```` json
{
  "header": {
    "source": "023-23",
    "code": -1,
    "message": "Failure",
    "system_time": 1633265128051,
    "tracking_id": "47e04087-6a6c-4a90-9425-86cc639dc7c8",
    "errors": [
      {
        "code": "40232307",
        "description": "Invalid application"
      }
    ]
  }
}
````

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>
