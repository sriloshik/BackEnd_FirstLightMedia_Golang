<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Add Attribute - API Specification

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

#### HTTP Method: Post

```
https://<server>/policy/urn/resource/attribute
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

#### Request Body:

<table width="100%">
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
    <td>Attribute Name.</td>
  </tr>
  <tr>
    <td>aty</td>
    <td>String</td>
    <td>Required</td>
    <td>Attribute Type Allowed values: platform, content, application, user, constant.</td>
  </tr>
  <tr>
    <td>dty</td>
    <td>String</td>
    <td>Required</td>
    <td>Attribute Data Type Allowed values: StringArray, String, Number, Boolean, DateTime.</td>
  </tr>
  <tr>
    <td>desc</td>
    <td>String</td>
    <td>Optinal</td>
    <td>Attribute Description.</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
POST https://server/policy/urn/resource/attribute
Authorization: Bearer <Access Token of IAM>
Content-Type: application/json
{
  "n": "attribute-1",
  "dty":"String",
  "aty":"constant"
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
    <td>Add attribute response</td>
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
    "source": "023-12",
    "code": 0,
    "message": "Success",
    "system_time": 1633104739470,
    "tracking_id": "02389ebc-ae0e-47b1-afd5-0c9a9166ab5d"
  },
  "data": {
    "aty": "constant",
    "ct": "2021-10-01T16:12:19Z",
    "dty": "String",
    "id": "0264029C-EC67-4D52-B5CE-F5FA318E07DF",
    "n": "aha",
    "t": "attribute",
    "u_id": "testproject_admin",
    "ut": "2021-10-01T16:12:19Z"
  }
}
```

### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>40231201</td>
    <td>Invalid Authorization</td>
  </tr>
  <tr>
    <td>40231202</td>
    <td>Application already exists</td>
  </tr>
  <tr>
    <td>40231290</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40231291</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure to add due to invalid or missing authorization token:

```json
{
  "header": {
    "source": "023-12",
    "code": -1,
    "message": "Failure",
    "system_time": 1622823186774,
    "tracking_id": "00ff6b8f-478f-445c-aa2a-665cc673b460",
    "errors": [
      {
        "code": "40231201",
        "description": "Invalid Authorization"
      }
    ]
  }
}
```

The following response is an example of failure due to attribute already existing in database:

```json
{
  "header": {
    "source": "023-12",
    "code": -1,
    "message": "Failure",
    "system_time": 1622823209173,
    "tracking_id": "50334706-f6d8-4d33-9130-0ee6ca511090",
    "errors": [
      {
        "code": "40231202",
        "description": "Attribute already exists"
      }
    ]
  }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>