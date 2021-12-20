<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Aggregate - API Specification

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
    <td>21 Sep 2021</td>
    <td>Manikanta Reddy</td>
    <td>Draft Version</td>
  </tr>
  <tr>
    <td>2</td>
    <td>   Sep 2021</td>
    <td>Senthilkumar Jeyarajan</td>
    <td>Reviewed and published</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: GET

```
https://<server>/user/usage/aggregate/{aty}/{field}
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

#### Request Body:

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
    <td>Unique identifier of the item.</td>
  </tr>
</table>


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
    <td>Page number</td>
  </tr>
    <tr>
    <td>pageSize</td>
    <td>String</td>
    <td>Optional</td>
    <td>Page size</td>
  </tr>
   <tr>
    <td>sortBy</td>
    <td>String</td>
    <td>Optional</td>
    <td>Sort field</td>
  </tr>
   <tr>
    <td>sortOrder</td>
    <td>String</td>
    <td>Optional</td>
    <td>Sort order - asc | desc</td>
  </tr>
  <tr>
    <td>groupBy</td>
    <td>String</td>
    <td>Optional</td>
    <td>Groupby - service | genre | network</td>
  </tr>
  <tr>
    <td>fromDate</td>
    <td>String</td>
    <td>Required</td>
    <td>From Date</td>
  </tr>
  <tr>
    <td>toDate</td>
    <td>String</td>
    <td>Optional</td>
    <td>To Date</td>
  </tr>
  <tr>
    <td>period</td>
    <td>String</td>
    <td>Required</td>
    <td>Period</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET https://server/user/usage/aggregate/{aty}/{field}
Authorization: Bearer <Access Token of IAM>

Content-Type: application/json

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
        "source": "045-01",
        "code": 0,
        "message": "Success",
        "system_time": 1631788837775,
        "tracking_id": "20bd6b4b-197b-43ee-b8d8-2edc49ad0f5d"
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
    <td>40460101</td>
    <td>Invalid or missing period</td>
  </tr>
  <tr>
    <td>40460102</td>
    <td>Invalid or missing from date</td>
  </tr>
  <tr>
    <td>40460103</td>
    <td>Invalid or missing to date</td>
  </tr>
  <tr>
    <td>40460104</td>
    <td>Invalid or missing group by</td>
  </tr>
  <tr>
    <td>40460105</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40460106</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40460107</td>
    <td>Invalid or missing sort order</td>
  </tr>
  <tr>
    <td>40460190</td>
    <td>System failure</td>
  </tr>
  <tr>
    <td>40460191</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to invalid X-Authorization request parameter,

```json


```

The following response is an example of failure due to invalid request payload,

```json
{
    "header": {
        "source": "045-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1631789153842,
        "tracking_id": "23d873d7-0ce5-4d2a-8921-176141b06b53",
        "errors": [
            {
                "code": "40450103",
                "description": "Invalid or missing item identifier"
            }
        ]
    }
}
```


<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>