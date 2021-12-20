<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Add Product - API Specification

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

#### HTTP Method: POST

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

#### Request Body

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
    <td>Product Code.</td>
  </tr>
  <tr>
    <td>desc</td>
    <td>String</td>
    <td>Optinal</td>
    <td>Product Description.</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
POST https://server/policy/urn/resource/product
Authorization: Bearer <Access Token of IAM>
Content-Type: application/json

{
  "n": "aha-1"
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
    <td>Add product response</td>
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
    "source": "023-02",
    "code": 0,
    "message": "Success",
    "system_time": 1633104457621,
    "tracking_id": "1b9fb73f-1c31-4bb6-8404-fb6f1510d728"
  },
  "data": {
    "ct": "2021-10-01T16:07:37Z",
    "id": "732915C9-5156-45D3-A5BF-A67EFAA8C9DA",
    "n": "aha-1",
    "t": "product",
    "u_id": "testproject_admin",
    "ut": "2021-10-01T16:07:37Z"
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
    <td>40230201</td>
    <td>Invalid X-Authorization</td>
  </tr>
  <tr>
    <td>40230202</td>
    <td>Product already exists</td>
  </tr>
  <tr>
    <td>40230290</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40230291</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure to add due to invalid or missing authorization token:

```json
{
  "header": {
    "source": "023-02",
    "code": -1,
    "message": "Failure",
    "system_time": 1622802219812,
    "tracking_id": "4807b319-213d-4b2a-a9b0-569cfe6a25e7",
    "errors": [
      {
        "code": "40230201",
        "description": "Invalid Authorization"
      }
    ]
  }
}
```

The following response is an example of failure due to product already existing in database:

```json
{
  "header": {
    "source": "023-02",
    "code": -1,
    "message": "Failure",
    "system_time": 1622802155395,
    "tracking_id": "d3456444-75b2-4387-a9a3-513daaeb4619",
    "errors": [
      {
        "code": "40230202",
        "description": "Product already exists"
      }
    ]
  }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>