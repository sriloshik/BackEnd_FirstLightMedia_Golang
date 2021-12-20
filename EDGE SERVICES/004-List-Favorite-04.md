<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## My List - Listings - API Specification

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
    <td>20 Sep 2021</td>
    <td>Manikanta Reddy</td>
    <td>Draft Version</td>
  </tr>
  <tr>
    <td>2</td>
    <td>04 Oct 2021</td>
    <td>Yashwanth Lakshmidhar</td>
    <td>Initial Review</td>
  </tr>
  <tr>
    <td>3</td>
    <td>05 Oct 2021</td>
    <td>Senthilkumar Jeyarajan</td>
    <td>Reviewed and Published</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: GET

```
https://<server>/user/favorite/list
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

<div class="page"/>

### Request query params

<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required / Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>pageNumber</td>
    <td>String</td>
    <td>Optional</td>
    <td>Number that indicates the page to retrieve of the paginated list of items. <br>Example: pageNumber=2 indicates second page.<br>Default value: 1.</td>
  </tr>
    <tr>
    <td>pageSize</td>
    <td>String</td>
    <td>Optional</td>
    <td>Number that indicates the number of records to return in response. <br>Example: pageSize=25 indicates to return 25 records per request. <br>Default value: 100.</td>
  </tr>
   <tr>
    <td>sortBy</td>
    <td>String</td>
    <td>Optional</td>
    <td>Field by which the items to be sorted. <br>Default value: timestamp.</td>
  </tr>
   <tr>
    <td>sortOrder</td>
    <td>String</td>
    <td>Optional</td>
    <td>Sort order. ascending (asc) or descending (desc).</td>
  </tr>
</table>


<hr style="height:1px;border-width:0;background-color:black">


#### Example Request

```json
GET https://server/user/favorite/list
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
    <td>itemId</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique identifier of item.</td>
  </tr>
  <tr>
    <td>ut</td>
    <td>String</td>
    <td>Required</td>
    <td>Last modified datetime.</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

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


#### Example OK Response

```json
{
  "header": {
    "source": "004-04",
    "code": "0",
    "message": "Success",
    "system_time": 1558041284123,
    "tracking_id": "fb8812b9-b5f7-472d-9ab2-8e662253ca03"
  },
  "data": [
    {
      "itemId": "item1",
      "ut": 1564394891
    },
    {
      "itemId": "item2",
      "ut": 1564394890
    }
  ]
}
```

### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>40040401</td>
    <td>Invalid X-Authorization</td>
  </tr>
  <tr>
    <td>40040402</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40040403</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40040404</td>
    <td>Invalid or missing sort by</td>
  </tr>
  <tr>
    <td>40040405</td>
    <td>Invalid or missing sort order</td>
  </tr>
  <tr>
    <td>40040406</td>
    <td>No records found</td>
  </tr>
  <tr>
    <td>40040490</td>
    <td>Subystem failure</td>
  </tr>
  <tr>
    <td>40040491</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to invalid X-Authorization request parameter,

```json
{
  "header": {
    "source": "004-04",
    "code": -1,
    "message": "Failure",
    "system_time": 1632133902720,
    "tracking_id": "eab5186a-5b79-45aa-bf77-d29e93361a8d",
    "errors": [
      {
        "code": "40040401",
        "description": "Invalid X-Authorization"
      }
    ]
  }
}
```

<br/>

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>