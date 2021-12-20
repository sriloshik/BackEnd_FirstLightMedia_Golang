<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## List Attribute - API Specification

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
    <td>String (UUID)</td>
    <td>Optional</td>
    <td>Unique identifier to trace the HTTP request for errors. The service will auto-generate a new identifier to return in the response if this parameter was not received.<br/>Example - fb8812b9-b5f7-472d-9ab2-8e662253ca03</td>
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
        <br/>Default value: Updated Time (ut)</td>
  </tr>
  <tr>
    <td>sortOrder</td>
    <td>String</td>
    <td>Optional</td>
    <td>Allowed values: asc or desc</td>
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
    <td>Product name. Required only when aty is ‘product’</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET http(s)://server/policy/urn/resource/attribute?aty=constant&pageNumber=1&pageSize=10&sortBy=ct&sortOrder=desc
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
    <td>List attribute response</td>
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
    "source": "023-15",
    "code": 0,
    "message": "Success",
    "system_time": 1623047661399,
    "start": 1,
    "rows": 2,
    "count": 2,
    "tracking_id": "c9fe1350-18ad-470d-8f88-3b7164e1979f"
  },
  "data": [
    {
      "aty": "constant",
      "ct": "2021-06-07T06:21:33Z",
      "dty": "String",
      "id": "CE3CB6E4-EEAD-4F8E-B244-B8579B5CEE53",
      "n": "attribute-2",
      "t": "attribute",
      "u_id": "user-id",
      "ut": "2021-06-07T06:21:33Z"
    },
    {
      "aty": "constant",
      "ct": "2021-06-04T16:11:31Z",
      "dty": "String",
      "id": "28E17201-3839-421C-8B33-AABB7EF10A23",
      "n": "attribute-1",
      "t": "attribute",
      "u_id": "user-id",
      "ut": "2021-06-04T16:11:31Z"
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
    <td>40231501</td>
    <td>Invalid or missing page number</td>
  </tr>
   <tr>
    <td>40231502</td>
    <td>Invalid or missing page size</td>
  </tr>
   <tr>
    <td>40231503</td>
    <td>Invalid or missing sort by</td>
  </tr>
   <tr>
    <td>40231504</td>
    <td>Invalid or missing sort order</td>
  </tr>
   <tr>
    <td>40231505</td>
    <td>Invalid or missing attribute type</td>
  </tr>
   <tr>
    <td>40231506</td>
    <td>Invalid or missing product name</td>
  </tr>
   <tr>
    <td>40231507</td>
    <td>No record found</td>
  </tr>
  <tr>
    <td>40231590</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40231591</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Error Samples

The following response is an example of no records found:

```` json
{
  "header": {
    "source": "023-15",
    "code": -1,
    "message": "Failure",
    "system_time": 1633093367566,
    "tracking_id": "abdfc24d-913f-43f5-bcb4-519c3b847870",
    "errors": [
      {
        "code": "40231507",
        "description": "No records found"
      }
    ]
  }
}
````

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>
