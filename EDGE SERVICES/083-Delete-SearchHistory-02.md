<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Delete Search History - API Specification

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
    <td>23 Sep 2021</td>
    <td>Manikanta Reddy</td>
    <td>Draft Version</td>
  </tr>
  <tr>
    <td>2</td>
    <td>06 Oct 2021</td>
    <td>Yashwanth Lakshmidhar</td>
    <td>Initial Review</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: DELETE

```
https://<server>/user/search/delete/{itemId}
```

#### Request Headers:

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
    <td>X-Authorization</td>
    <td>String</td>
    <td>Required</td>
    <td>Access Token of <b>User Management System</b> to identify the user.</td>
  </tr>
  <tr>
    <td>X-Tracking-Id</td>
    <td>String</td>
    <td>Optional</td>
    <td>Unique identifier to trace the HTTP request for errors. The service will auto-generate a new identifier to return in the response if this parameter was not received.<br/>Example - fb8812b9-b5f7-472d-9ab2-8e662253ca03</td>
  </tr>
</table>


<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Path Parameters

<table width="100%">
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>itemId</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique identifier of the item. This could be the content identifier or the resource identifier.</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/> 

#### Example Request

```json
DELETE https://server/user/history/delete/comedy
Authorization: Bearer <Access Token of IAM>
X-Authorization: Access Token of User Management System to identify the user.

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
    <td>Delete search history response</td>
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
    "source": "083-02",
    "code": 0,
    "message": "Success",
    "system_time": 1624623456229,
    "tracking_id": "0bd5c228-bdd7-43ec-a9f7-a3c0128cdcb6"
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
    <td>40830201</td>
    <td>Invalid X-Authorization</td>
  </tr>
  <tr>
    <td>40830202</td>
    <td>Item not found</td>
  </tr>
  <tr>
    <td>40830290</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40830291</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to invalid X-Authorization request parameter,

```json
{
  "header": {
    "source": "083-02",
    "code": -1,
    "message": "Failure",
    "system_time": 1632391232310,
    "tracking_id": "0e1a2c62-c3ce-499a-95d5-e3597da2a12f",
    "errors": [
      {
        "code": "40830201",
        "description": "Invalid X-Authorization"
      }
    ]
  }
}
```

The following response is an example of failure due to item not found,

```json
{
  "header": {
    "source": "083-02",
    "code": -1,
    "message": "Failure",
    "system_time": 1632393307819,
    "tracking_id": "fbf21843-1fc7-4b10-91ae-78f6b9383f79",
    "errors": [
      {
        "code": "40830203",
        "description": "Item not found"
      }
    ]
  }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>