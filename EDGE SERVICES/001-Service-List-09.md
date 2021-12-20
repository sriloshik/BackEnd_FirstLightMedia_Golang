<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Service List - API Specification

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
    <td>01 Aug 2021</td>
    <td>Manikanta Reddy</td>
    <td>Draft Version</td>
  </tr>
  <tr>
    <td>2</td>
    <td>01 Oct 2021</td>
    <td>Yashwanth Lakshmidhar</td>
    <td>Initial Review</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: GET

```
https://<server>/remote/config/services
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
    <td>String</td>
    <td>Optional</td>
    <td>Unique identifier to trace the HTTP request for errors. The service will auto-generate a new identifier to return in the response if this parameter was not received.<br/>Example - fb8812b9-b5f7-472d-9ab2-8e662253ca03</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET https://server/remote/config/services
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

#### Response Body

<table width='100%'>
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>services</td>
    <td>String</td>
    <td>Required</td>
    <td>List of services to be consumed</td>
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
		"source": "001-09",
		"code": 0,
		"message": "Success",
		"system_time": 1598441510614,
		"tracking_id": "a97f11e2-947d-42b2-baac-cd5ba80d406d"
	},
	"data": {
		"services": {
			"bookmark": "https://bookmark.sbox.edge.firstlight.ai",
			"catalog": "https://catalog.sbox.edge.firstlight.ai",
			"epg": "https://epg-gateway.sbox.edge.firstlight.ai",
			"favorite": "https://favorite.sbox.edge.firstlight.ai",
			"heartbeat": "https://heartbeat.sbox.edge.firstlight.ai",
			"image": "https://image-resizer.sbox.edge.firstlight.ai",
			"live": "https://live-metadata.sbox.edge.firstlight.ai",
			"playback": "https://playback-auth.sbox.edge.firstlight.ai",
			"register": "https://device-register.sbox.edge.firstlight.ai",
			"storefront": "https://storefront.sbox.edge.firstlight.ai",
			"stream": "https://stream.sbox.edge.firstlight.ai",
			"vod": "https://metadata.sbox.edge.firstlight.ai"
		}
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
    <td>40010901</td>
    <td>Service list not found</td>
  </tr>
    <td>40010990</td>
    <td>Subystem failure</td>
  </tr>
  <tr>
    <td>40010991</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to missing or invalid service list,

```json
{
  "header": {
    "source": "001-09",
    "code": -1,
    "message": "Failure",
    "system_time": 1632214778612,
    "tracking_id": "8c17ad3b-a181-435f-a37a-2b0f6656d9d4",
    "errors": [
      {
        "code": "40010901",
        "description": "Service list not found"
      }
    ]
  }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>