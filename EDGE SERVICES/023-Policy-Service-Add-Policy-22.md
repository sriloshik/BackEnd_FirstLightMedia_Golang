<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Add Policy - API Specification

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

#### HTTP Method: POST

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
    <td>appliesifAll</td>
    <td>JSON Object Array</td>
    <td>Required when appliesifAny is not present</td>
    <td>Match all conditions
        <br/>Policy will be applied only if all of the conditions are satisfied.</td>
  </tr>
  <tr>
    <td>appliesifAny</td>
    <td>JSON Object Array</td>
    <td>Required when appliesifAll is not present</td>
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
    <td>Required</td>
    <td>Publication Status
        <br/>Allowed values : published, draft, archived</td>
  </tr>
  <tr>
    <td>ef</td>
    <td>JSON Object Array</td>
    <td>Required</td>
    <td>Effects
        <br/>Result value to be considered after evaluating the policy</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
POST https://server/policy/urn/resource/rule
Authorization: Bearer <Access Token of IAM>
Content-Type: application/json

{
  "t": "policy",
  "pty": "application",
  "u_id": "user-id",
  "id": "a8ae57a5-1d69-4c77-9698-c525fc291445",
  "pn": "sample-ott-product",
  "an": "sample-ott-application",
  "st": "draft",
  "n": "ios_only",
  "desc": "rule to allow only ios devices",
  "appliesifAll": [
    {
      "n": "device_type",
      "aty": "platform",
      "op": "equals",
      "val": "iosmobile"
    }
  ]
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
    <td>Add policy response</td>
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
    "source": "023-22",
    "code": 0,
    "message": "Success",
    "system_time": 1633504859544,
    "tracking_id": "2d4d1e1d-bc5b-4b23-95c9-ee581471d397"
  },
  "data": {
    "an": "playback-auth-service",
    "appliesifAll": [
      {
        "aty": "product",
        "n": "reg",
        "op": "oneof",
        "val": "country"
      }
    ],
    "ct": "2021-10-06T07:20:59Z",
    "ef": [
      {
        "key": "action.allow",
        "type": "Boolean",
        "value": true
      }
    ],
    "id": "359acc9b-ed99-487f-a0ac-d19aafc01aaa",
    "key": "359acc9b-ed99-487f-a0ac-d19aafc01aaa-1633504859",
    "n": "generic-country-policy",
    "pn": "aha",
    "pty": "application",
    "st": "draft",
    "t": "policy",
    "u_id": "manogars",
    "ut": "2021-10-06T07:20:59Z"
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
    <td>40232201</td>
    <td>Invalid Authorization</td>
  </tr>
  <tr>
    <td>40232202</td>
    <td>Invalid input status</td>
  </tr>
  <tr>
    <td>40232203</td>
    <td>Invalid product</td>
  </tr>
  <tr>
    <td>40232204</td>
    <td>Invalid application</td>
  </tr>
  <tr>
    <td>40232205</td>
    <td>Invalid attribute</td>
  </tr>
  <tr>
    <td>40232206</td>
    <td>Invalid lookup</td>
  </tr>
  <tr>
    <td>40232290</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40232291</td>
    <td>Unknown failure</td>
  </tr>
</table>

#### Error Samples
The following response is an example of failure due to invalid attribute:

```` json
{
  "header": {
    "source": "023-22",
    "code": -1,
    "message": "Failure",
    "system_time": 1633233442120,
    "tracking_id": "7868a278-3d5c-40d5-82ba-c4ba5075f2ff",
    "errors": [
      {
        "code": "40232205",
        "description": "Invalid attribute"
      }
    ]
  }
}
````

The following response is an example of failure due to invalid product:

```` json
{
  "header": {
    "source": "023-22",
    "code": -1,
    "message": "Failure",
    "system_time": 1633233528314,
    "tracking_id": "59196842-e2c5-4a87-afe4-22c90409ba53",
    "errors": [
      {
        "code": "40232203",
        "description": "Invalid product"
      }
    ]
  }
}
````
<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>
