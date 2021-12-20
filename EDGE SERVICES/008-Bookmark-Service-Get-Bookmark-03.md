<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Continue Watching - Get player offset - API Specification

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
https://<server>/user/bookmark/lookup/{itemId}
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
GET https://server/user/bookmark/lookup/content123
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
    <td>Unique identifier of the item.</td>
  </tr>
  <tr>
    <td>offset</td>
    <td>Number</td>
    <td>Required</td>
    <td>Number (in milliseconds) that indicates the video watch progress of the content from its start position.</td>
  </tr>
    <tr>
    <td>seasonId</td>
    <td>String</td>
    <td>Required when episodeId is present</td>
    <td>Unique identifier of the season</td>
  </tr>
  <tr>
    <td>episodeId</td>
    <td>String</td>
    <td>Required when seasonId is present</td>
    <td>Unique identifier of the episode</td>
  </tr>
  <tr>
    <td>ut</td>
    <td>Number(Time in Epoch format)</td>
    <td>Required</td>
    <td>Last updated time of bookmark record</td>
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

The following is an example of standalone title bookmark. Ex: movie, shortvideo

```json
{
  "header": {
    "source": "008-03",
    "code": 0,
    "message": "Success",
    "system_time": 1632115033238,
    "tracking_id": "b7582c01-c736-425e-b499-e3f8b0a26f7f"
  },
  "data": {
    "itemId": "content123",
    "offset": 12000,
    "ut": 1631888475177
  }
}
```

<div class="page"/>

The following is an example of series bookmark

```json
{
  "header": {
    "source": "008-03",
    "code": 0,
    "message": "Success",
    "system_time": 1633147564642,
    "tracking_id": "bbaf13f6-fedc-46df-a7bc-22b259ab73b3"
  },
  "data": {
    "episodeId": "8c554764-1ed1-4a22-b662-1300b4151a06",
    "itemId": "content123",
    "offset": 600,
    "seasonId": "58955452-d24f-4c67-aac9-12744ede7ddd",
    "ut": 1633147530854
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
    <td>40080301</td>
    <td>Invalid X-Authorization</td>
  </tr>
  <tr>
    <td>40080302</td>
    <td>Invalid or missing item identifier</td>
  </tr>
  <tr>
    <td>40080303</td>
    <td>Item not found</td>
  </tr>
  </tr>
  <tr>
    <td>40080390</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40080391</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

### Error Samples

The following response is an example of failure due to invalid X-Authorization request parameter:

```json
{
  "header": {
    "source": "008-03",
    "code": -1,
    "message": "Failure",
    "system_time": 1632114303952,
    "tracking_id": "6385baf8-91af-4a33-9532-74c171b87260",
    "errors": [
      {
        "code": "40080301",
        "description": "Invalid X-Authorization"
      }
    ]
  }
}
```

The following response is an example of failure due to Item not found:

```json
{
  "header": {
    "source": "008-03",
    "code": -1,
    "message": "Failure",
    "system_time": 1632115221602,
    "tracking_id": "dfd56ecf-56b7-4748-868d-41ee96c52351",
    "errors": [
      {
        "code": "40080303",
        "description": "Item not found"
      }
    ]
  }
}
```

<br/>

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>