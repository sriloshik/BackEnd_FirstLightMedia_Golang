<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Device Register - API Specification

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
    <td>Manogar Subramani</td>
    <td>Draft Version</td>
  </tr>
  <tr>
    <td>2</td>
    <td>15 Sep 2021</td>
    <td>Senthilkumar Jeyarajan</td>
    <td>Reviewed and published</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: POST

```
https://<server>/device/app/register
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
    <td>X-Client-Id</td>
    <td>String</td>
    <td>Optional</td>
    <td>Unique identifier of the device type to apply policies as configured.</td>
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
    <td>uniqueId</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique identifier of the device.</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
POST https://server/device/app/register
Authorization: Bearer <Access Token of IAM>
X-Authorization: Access Token of User Management System to identify the user.
Content-Type: application/json

{
  "uniqueId": "12123JNBIKAJU21412"
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
  <tr>
    <td>secret</td>
    <td>String</td>
    <td>Required</td>
    <td>Secret that shall be used by the client library to sign the JWT token with device ID as claim.</td>
  </tr>
  <tr>
    <td>deviceId</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique identifier of the device.</td>
  </tr>
  <tr>
    <td>expiry</td>
    <td>Number</td>
    <td>Required</td>
    <td>Expiration (in seconds) to use when generating the JWT token by the client library.</td>
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
    "source": "002-01",
    "code": 0,
    "message": "Success",
    "system_time": 1594152509926,
    "tracking_id": "dfb0b8aa-50e6-4303-9234-e957ccd20df7"
  },
  "data": {
    "secret": "l+LF7F3jPsVSvhmqXr4njSDFBr59NQCIgZ/y/f23mqg=",
    "expiry": 30,
    "deviceId": "test_device_01"
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
    <td>40020101</td>
    <td>Invalid X-Authorization</td>
  </tr>
  <tr>
    <td>40020102</td>
    <td>Invalid or missing device identifier</td>
  </tr>
  <tr>
    <td>40020190</td>
    <td>System failure</td>
  </tr>
  <tr>
    <td>40020191</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to invalid X-Authorization request parameter,

```json
{
  "header": {
    "source": "002-01",
    "code": -1,
    "message": "Failure",
    "system_time": 1558041284123,
    "tracking_id": "fb8812b9-b5f7-472d-9ab2-8e662253ca03",
    "errors": [
      {
        "code": "40020101",
        "description": "Invalid X-Authorization"
      }
    ]
  }
}
```

The following response is an example of failure due to invalid request payload,

```json
{
  "header": {
    "source": "002-01",
    "code": -1,
    "message": "Failure",
    "system_time": 1558041284123,
    "tracking_id": "fb8812b9-b5f7-472d-9ab2-8e662253ca03",
    "errors": [
      {
        "code": "40020102",
        "description": "Invalid or missing device identifier"
      }
    ]
  }
}
```

<br/>

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>