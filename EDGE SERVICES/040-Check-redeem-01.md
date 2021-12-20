<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Check Redeem - API Specification

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
    <td>20 Aug 2021</td>
    <td>Manikanta Reddy</td>
    <td>Draft Version</td>
  </tr>
  <tr>
    <td>2</td>
    <td> Sep 2021</td>
    <td>Senthilkumar Jeyarajan</td>
    <td>Reviewed and published</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: POST

```
https://<server>/media/content/checkredeem
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
    <td>deviceId</td>
    <td>String</td>
    <td>Required</td>
    <td>Signed Device ID token.</td>
  </tr>
  <tr>
    <td>contentId</td>
    <td>String</td>
    <td>Required</td>
    <td>Video content identifier.</td>
  </tr>
  <tr>
    <td>contentTypeId</td>
    <td>String</td>
    <td>Required</td>
    <td>Video content type. <br/>
    Allowed values are; live | vod</td>
  </tr>
  <tr>
    <td>catalogType</td>
    <td>String</td>
    <td>Required</td>
    <td>Video catalog type. <br/>
    Allowed values are; movie | tvepisode | channel | sportliveevent | webepisode | shortvideo | trailer | sportshow | sportevent | sporthighlight | sportclip</td>
  </tr>
  <tr>
    <td>delivery</td>
    <td>String</td>
    <td>Required</td>
    <td>Delivery type requested. <br/>
    Allowed values are; streaming | download</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
POST https://server/media/content/checkredeem
Authorization: Bearer <Access Token of IAM>
X-Authorization: Access Token of User Management System to identify the user.
Content-Type: application/json

{
	"deviceId": "firstlight-device-001",
	"contentId": "14C9F89D-00C9-432B-82D8-A60D80CCCBB7",
	"contentTypeId": "vod",
	"catalogType": "movie",
	"delivery": "streaming"
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

```

### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>40400101</td>
    <td>Invalid X-Authorization</td>
  </tr>
  <tr>
    <td>40400102</td>
    <td>Invalid X-Device-Id</td>
  </tr>
  <tr>
    <td>40400103</td>
    <td>Missing or invalid content identifier</td>
  </tr>
  <tr>
    <td>40400104</td>
    <td>Missing or invalid device identifier</td>
  </tr>
  <tr>
    <td>40400105</td>
    <td>Missing or invalid content type identifier</td>
  </tr>
  <tr>
    <td>40400106</td>
    <td>Missing or invalid catalog type</td>
  </tr>
  <tr>
    <td>40400107</td>
    <td>Missing or invalid delivery type</td>
  </tr>
  <tr>
    <td>40400108</td>
    <td>Missing or invalid client identifier</td>
  </tr>
  <tr>
    <td>40400120</td>
    <td>Invalid content metadata</td>
  </tr>
  <tr>
    <td>40400121</td>
    <td>Missing or invalid client identifier</td>
  </tr>
  <tr>
    <td>40400140</td>
    <td>Not entitled to redeem</td>
  </tr>
  <tr>
    <td>40400190</td>
    <td>System failure</td>
  </tr>
  <tr>
    <td>40400191</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to invalid X-Authorization request parameter,

```json
{
    "header": {
        "source": "040-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1632129824633,
        "tracking_id": "b9691d7b-8c6f-430a-a2a6-504ab67ff133",
        "errors": [
            {
                "code": "40400101",
                "description": "Invalid X-Authorization"
            }
        ]
    }
}
```

The following response is an example of failure due to invalid ip address,

```json
{
    "header": {
        "source": "040-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1632129860823,
        "tracking_id": "d8dad224-1787-49ba-ae31-14a21ce53f44",
        "errors": [
            {
                "code": "40400140",
                "description": "Not entitled to redeem"
            }
        ]
    }
}
```
The following response is an example of failure due to invalid catalog type,

```json
{
    "header": {
        "source": "040-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1632223059175,
        "tracking_id": "359ba3c8-d744-430d-8306-2f03039779ff",
        "errors": [
            {
                "code": "40400106",
                "description": "Missing or invalid catalog type"
            }
        ]
    }
}
```
The following response is an example of failure due to invalid delivery type,

```json
{
    "header": {
        "source": "040-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1632223163904,
        "tracking_id": "8e6723ca-77a2-462c-aedc-a14b66594850",
        "errors": [
            {
                "code": "40400107",
                "description": "Missing or invalid delivery type"
            }
        ]
    }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>