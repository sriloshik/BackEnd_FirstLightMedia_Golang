<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## List config- API Specification

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
https://<server>/remote/config/list
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

#### Request Query Parameters

<table width='100%'>
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
 <tr>
    <td>st</td>
    <td>String</td>
    <td>Optional</td>
    <td>Content status. <br/>Allowed values are; published | draft | archived</td>
  </tr>
   <tr>
    <td>pageNumber</td>
    <td>String</td>
    <td>Optional</td>
    <td>Page Number</td>
  </tr> <tr>
    <td>pageSize</td>
    <td>String</td>
    <td>Optional</td>
    <td>Page Size. <br/>Allowed values are between 1 and 100</td>
  </tr> <tr>
    <td>sortBy</td>
    <td>String</td>
    <td>Optional</td>
    <td>Sort by field</td>
  </tr> <tr>
    <td>sortOrder</td>
    <td>String</td>
    <td>Optional</td>
    <td>Sort Order. <br/>Allowed values are; asc | desc</td>
  </tr>
  </table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET https://server/remote/config/list
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
    <td>n</td>
    <td>String</td>
    <td>Required</td>
    <td>Config Name</td>
  </tr>
  <tr>
    <td>id</td>
    <td>String</td>
    <td>Required</td>
    <td>Config Id</td>
  </tr>
  <tr>
    <td>key</td>
    <td>String</td>
    <td>Required</td>
    <td>Config Document key</td>
  </tr>
  <tr>
    <td>t</td>
    <td>String</td>
    <td>Required</td>
    <td>Resource Type.<br/> Allowed values: config</td>
  </tr>
  <tr>
    <td>appliesif</td>
    <td>JSON Object Array</td>
    <td>Required</td>
    <td>Match all conditions
        <br/>Config will be applied and returned only if all of the conditions are satisfied.</td>
  </tr>
  <tr>
    <td>attrs</td>
    <td>JSON Object Array</td>
    <td>Required</td>
    <td>The attributes list to be returned</td>
  </tr>
  <tr>
    <td>d</td>
    <td>String</td>
    <td>Optional</td>
    <td>Config Description</td>
  </tr>
  <tr>
    <td>st</td>
    <td>String</td>
    <td>Required</td>
    <td>Publication Status</td>
  </tr>
  <tr>
    <td>ct</td>
    <td>String</td>
    <td>Required</td>
    <td>Created time</td>
  </tr>
  <tr>
    <td>ut</td>
    <td>String</td>
    <td>Required</td>
    <td>Updated time</td>
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
    "source": "001-06",
    "code": 0,
    "message": "Success",
    "system_time": 1631869196459,
    "start": 1,
    "rows": 10,
    "count": 15,
    "tracking_id": "c00d8339-2ad9-4a48-9039-62ec3f79b066"
  },
  "data": [
    {
      "appliesif": [
        {
          "name": "app",
          "value": "console"
        },
        {
          "name": "type",
          "value": "recommendations"
        }
      ],
      "attrs": [
        {
          "key": "labels",
          "type": "String",
          "value": "More like this,Most popular,Because you watched,Recommended for you,Trending now"
        },
        {
          "default": true,
          "field": "cty",
          "key": "Content Type",
          "type": "String",
          "value": "Movie,TVSeries,TVEpisode,SportShow,SportHighlight,SportClip,SportEvent"
        }
      ],
      "ct": "2021-08-27T12:49:45Z",
      "d": "Recommendations Filters used for CMS Curation",
      "id": "83B0CB8B-947A-44D3-9361-618B3AD729FB",
      "key": "83B0CB8B-947A-44D3-9361-618B3AD729FB-1630068423",
      "n": "cms_curation_recommendations",
      "st": "published",
      "t": "config",
      "ut": "2021-08-27T12:49:45Z"
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
    <td>40010601</td>
    <td>Invalid page number</td>
  </tr>
  <tr>
    <td>40010602</td>
    <td>Invalid page size</td>
  </tr>
  <tr>
    <td>40010603</td>
    <td>Invalid sort by</td>
  </tr>
  <tr>
    <td>40010604</td>
    <td>Invalid sort order</td>
  </tr>
  <tr>
    <td>40010605</td>
    <td>Invalid status</td>
  </tr>
  <tr>
    <td>40010606</td>
    <td>Config not exists</td>
  </tr>
  <tr>
    <td>40010690</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40010691</td>
    <td>Unknown failure</td>
  </tr>
</table>

### Error Samples

The following response is an example of failure when Config not found:

```json
{
	"header": {
		"source": "001-06",
		"code": -1,
		"message": "Failure",
		"system_time": 1588074996859,
		"tracking_id": "e9150dac-d65e-4e1b-8548-169728de7f29",
		"errors": [
			{
				"code": "40010605",
				"description": "Config not exists"
			}
		]
	}
}
```
<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>