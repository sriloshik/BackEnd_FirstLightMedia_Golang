<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Count Attribute - API Specification

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
https://<server>/count/urn/resource/attribute
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

#### Request Parameters

<table width='100%'>
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>aty</td>
    <td>String</td>
    <td>Optional</td>
    <td>Attribute type. Allowed values: platform, product, content, application, user, constant.</td>
  </tr>
  <tr>
    <td>pn</td>
    <td>String</td>
    <td>Required(conditional)</td>
    <td>Product name. Required only when aty is 'product'</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET https://server/count/urn/resource/attribute?aty=constant
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
    <td>Count attributes response</td>
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
    "source": "023-16",
    "code": 0,
    "message": "Success",
    "system_time": 1623048504228,
    "tracking_id": "5b78b07b-f223-4648-a6f7-3024f7834bf0"
  },
  "data": {
    "count": 3
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
    <td>40231601</td>
    <td>Invalid or missing attribute type</td>
  </tr>
  <tr>
    <td>40231602</td>
    <td>Invalid or missing product name</td>
  </tr>
  <tr>
    <td>40231690</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40231691</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Error Samples
The following response is an example of invalid or missing attribute type:

```` json
{
  "header": {
    "source": "023-16",
    "code": -1,
    "message": "Failure",
    "system_time": 1633093000432,
    "tracking_id": "1563a41a-ae9b-4d7c-8d49-b37254e744c5",
    "errors": [
      {
        "code": "40231601",
        "description": "Invalid or missing attribute type"
      }
    ]
  }
}
````

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>
