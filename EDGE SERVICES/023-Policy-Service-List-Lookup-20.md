<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## List Lookup - API Specification

### Version History

<table width='100%'>
  <tr>
    <th width='20%'>S.No</th>̌
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
    <td>Manogar Subramani</td>̌
    <td>Initial review completed</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: GET

```
https://<server>/policy/urn/resource/lookup
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
        <br/>Default value: Updated Time(ut)</td>
  </tr>
  <tr>
    <td>sortOrder</td>
    <td>String</td>
    <td>Optional</td>
    <td>Allowed values: asc or desc</td>
  </tr>
  <tr>
    <td>lty</td>
    <td>String</td>
    <td>Optional</td>
    <td>Lookup type Allowed values: platform, content, application, user.</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET http(s)://server/policy/urn/resource/lookup?lty=content&pageNumber=1&pageSize=10&sortBy=ct&sortOrder=desc
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
    <td>List lookup response</td>
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
    "source": "023-20",
    "code": 0,
    "message": "Success",
    "system_time": 1623054863401,
    "start": 1,
    "rows": 2,
    "count": 2,
    "tracking_id": "275c628b-6010-460a-ab49-858ea75635e0"
  },
  "data": [
    {
      "ct": "2021-06-07T07:22:40Z",
      "d": [
        "value"
      ],
      "desc": "Lookup Description",
      "dty": "StringArray",
      "id": "2162BC93-B26D-4E46-AD1D-2B66EE36B18F",
      "lty": "content",
      "n": "lookup-2",
      "t": "lookup",
      "u_id": "user-id",
      "ut": "2021-06-07T07:31:38Z"
    },
    {
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
    <td>40232001</td>
    <td>Invalid or missing page number</td>
  </tr>
   <tr>
    <td>40232002</td>
    <td>Invalid or missing page size</td>
  </tr>
   <tr>
    <td>40232003</td>
    <td>Invalid or missing sort by</td>
  </tr>
   <tr>
    <td>40232004</td>
    <td>Invalid or missing sort order</td>
  </tr>
   <tr>
    <td>40232005</td>
    <td>Invalid or missing lookup type</td>
  </tr>
   <tr>
    <td>40232006</td>
    <td>No record found</td>
  </tr>
  <tr>
    <td>40232090</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40232091</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Error Samples
The following response is an example of no records found:

```` json
{
  "header": {
    "source": "023-20",
    "code": -1,
    "message": "Failure",
    "system_time": 1633093425901,
    "tracking_id": "8a72ba14-5b30-46c3-82fe-3ab7f7c86ba3",
    "errors": [
      {
        "code": "40232006",
        "description": "No records found"
      }
    ]
  }
}
````

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>
