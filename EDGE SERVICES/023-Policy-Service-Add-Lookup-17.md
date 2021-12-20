<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Add Lookup - API Specification

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
https://<server>/policy/urn/resource/lookup
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
    <td>Lookup Name</td>
  </tr>
  <tr>
    <td>lty</td>
    <td>String</td>
    <td>Required</td>
    <td>Lookup Type, Allowed Values : platform, content, application, user</td>
  </tr>
  <tr>
    <td>dty</td>
    <td>String</td>
    <td>Required</td>
    <td>Lookup Data Type, Allowed Values : StringArray</td>
  </tr>
  <tr>
    <td>d</td>
    <td>String Array</td>
    <td>Required</td>
    <td>Lookup Data</td>
  </tr>
  <tr>
    <td>desc</td>
    <td>String</td>
    <td>Optional</td>
    <td>Lookup Description</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```` json
POST https://server/policy/urn/resource/lookup
Authorization: Bearer <Access Token of IAM>
Content-Type: application/json

{
  "n": "lookup-1",
  "lty": "content",
  "dty": "StringArray",
  "d": [
    "value-1"
  ]
}
````

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
    <td>Add lookup response</td>
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
    "source": "023-17",
    "code": 0,
    "message": "Success",
    "system_time": 1623049492302,
    "tracking_id": "4df863e1-c844-4b10-a0e7-57e7ff80cf0b"
  },
  "data": {
    "ct": "2021-06-07T07:04:52Z",
    "d": [
      "value"
    ],
    "dty": "StringArray",
    "id": "1849E8EC-E509-4707-B990-26D2CC6B8CE6",
    "lty": "content",
    "n": "lookup-1",
    "t": "lookup",
    "u_id": "user-id",
    "ut": "2021-06-07T07:04:52Z"
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
    <td>40231701</td>
    <td>Invalid Authorization</td>
  </tr>
  <tr>
    <td>40231702</td>
    <td>Lookup name already exists</td>
  </tr>
  <tr>
    <td>40231790</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40231791</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Error Samples
The following response is an example of failure due to lookup name already existing in database:

```` json
{
  "header": {
    "source": "023-17",
    "code": -1,
    "message": "Failure",
    "system_time": 1633091581943,
    "tracking_id": "2bf4b275-c3e9-4763-9a0a-3428009c61e9",
    "errors": [
      {
        "code": "40231702",
        "description": "Lookup name already exists"
      }
    ]
  }
}
````

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>
