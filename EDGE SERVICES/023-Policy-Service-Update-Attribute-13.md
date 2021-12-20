<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Update Attribute - API Specification

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

#### HTTP Method: PUT

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
    <td>id</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique Identifier of Resource.</td>
  </tr>
  <tr>
    <td>n</td>
    <td>String</td>
    <td>Required</td>
    <td>Application Name.</td>
  </tr>
  <tr>
    <td>aty</td>
    <td>String</td>
    <td>Required</td>
    <td>Attribute Type, Allowed values: platform, content, application, user, constant.</td>
  </tr>
  <tr>
    <td>dty</td>
    <td>String</td>
    <td>Required</td>
    <td>Attribute Data Type, Allowed values: StringArray, String, Number, Boolean, DateTime..</td>
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
PUT https://server/policy/urn/resource/attribute
Authorization: Bearer <Access Token of IAM>
Content-Type: application/json
{
  "n": "Aha-1",
  "t": "application",
  "u_id": "testproject_admin",
  "dty": "String",
  "aty": "constant"
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
    <td>Update attribute response</td>
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
    "system_time": 1633107873754,
    "tracking_id": "064ce2a1-0b23-4c1e-998b-6f8fb5267f8d"
  },
  "data": {
    "aty": "constant",
    "ct": "2021-10-01T17:04:33Z",
    "dty": "String",
    "id": "1867592A-C49D-49E0-BC1F-E1DBE0FA651D",
    "n": "Aha-1",
    "t": "attribute",
    "u_id": "testproject_admin",
    "ut": "2021-10-01T17:04:33Z"
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
    <td>40231301</td>
    <td>Invalid Authorization</td>
  </tr>
  <tr>
    <td>40231302</td>
    <td>Attribute already exists</td>
  </tr>
  <tr>
    <td>40231303</td>
    <td>Product not exists</td>
  </tr>
  <tr>
    <td>40231304</td>
    <td> Item not found</td>
  </tr>
  <tr>
    <td>40231305</td>
    <td> Update not allowed for the attribute type</td>
  </tr>
  <tr>
    <td>40231390</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40231391</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to attribute type not allowed to be updated:

```json
{
  "header": {
    "source": "023-13",
    "code": -1,
    "message": "Failure",
    "system_time": 1633163476700,
    "tracking_id": "c6e36e0e-e482-4fa0-9a3c-712099a781d1",
    "errors": [
      {
        "code": "40231305",
        "description": "Update not allowed for the attribute type"
      }
    ]
  }
}
```

The following response is an example of failure due to schema validation failure:

```json
{
  "header": {
    "source": "023-13",
    "code": -1,
    "message": "Failure",
    "system_time": 1633163790583,
    "tracking_id": "d6720679-4df7-4f35-8495-312751adcb7d",
    "errors": [
      {
        "code": "40231350",
        "description": "pn: String length must be greater than or equal to 1"
      }
    ]
  }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>