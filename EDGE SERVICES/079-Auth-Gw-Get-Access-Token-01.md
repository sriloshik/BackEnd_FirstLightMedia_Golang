<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Token Generation - API Specification

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
    <td>05 Oct 2021</td>
    <td>Tulaja Nandewar</td>
    <td>Draft Version</td>
  </tr>
  <tr>
    <td>2</td>
    <td> Oct 2021</td>
    <td>Manogar Subramani</td>
    <td>Initial review completed</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: POST

```
https://<server>platform/access/token

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
    <td>String</td>
    <td>Optional</td>
    <td>Unique identifier to trace the HTTP request for errors. The service will auto-generate a new identifier to return in the response if this parameter was not received.<br/>Example - fb8812b9-b5f7-472d-9ab2-8e662253ca03</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Request Body

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
    <td>Unique identifier of the device.</td>
  </tr>
  <tr>
    <td>deviceName</td>
    <td>String</td>
    <td>Optional</td>
    <td>Unique name assigned to the device platform.
        <br/>Allowed values are; iosmobile | iostablet | tvos | androidmobile | androidtablet | 
        <br/>androidtv | androidstb | web | mobileweb | samsungtizentv | lgwebostv | rokutv | ps4 | ps5 | xbox | x1 | castclient</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Example Request

```json
POST https://server/platform/access/token
Authorization: Bearer <Access Token of IAM>
{
    "deviceId": "firstlight-device-001",
    "deviceName": "androidmobile"
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
    <td>token</td>
    <td>String</td>
    <td>Required</td>
    <td>Returns access token</td>
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

The following response is an example of a successful token generation response:
```json
{
    "header": {
        "source": "079-01",
        "code": 0,
        "message": "Success",
        "system_time": 1633419580353,
        "tracking_id": "e7703957-cef1-4a45-b0ec-b21c788b774e"
    },
    "data": {
        "token": "eyJhbGciOiJkaXIiLCJlbmMiOiJBMjU2R0NNIiwidHlwIjoiSldUIn0..o6bxxykqcsSnbz8p.RD11V6Y2Zn8ja-xENCqKSCtXOZoSwRFIO-ySquV9hrBlMW9yExt_daZ9Xdai8WrI_RQHWsXV8HEzrHQ9YhQx2k4BRH6t4E1HLYTeKN8sWJ4VPE1isjKGhnFSmb0tKwvOvbf15pqcSr9V_8S2_FB5STIc8UwGEo0f10IpG8ugQhC7g2XDfITke405sZY5n-w-HdoVZrr_rJ3Eb4pzaqoZWSaDmifBJrEacYwbdeKxJeLIoXcT0J9GM25vxAedEovjJo0g2BGr-TM7W9WAHYGQK7txY5SmuoAjs_-cGMaavWAbN4zmoO0ksCXp2Uj--YmvUinNSCiaD5HM8TJS8vCSsGOS88sNt_r-yyc1ZkTNSy9_uR3_Z9pWDdKhVsVgx2ZyLSPAQu69NXQIbI4FQah2AbunQSNSY3tmh1qHnKaZkafUo2QN9nQkWgyjxW-IvEINwJpJRt6C6_3egxTe1eI_JtnKFWVrQe47epgiX9ORAtbQv7pOLKpIwzrI1G_HZFqdE73Gyr2vIrRQjqbhjUpCzw.87vbqxVjJSEFCDTn4cHAAA"
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
    <td>40790101</td>
    <td>Missing or invalid device identifier</td>
  </tr>
  <tr>
    <td>40790102</td>
    <td>Missing or invalid device type</td>
  </tr>
  <tr>
    <td>40790190</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40790191</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of request validation failure :
```json
{
    "header": {
        "source": "079-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1633420156474,
        "tracking_id": "63fe1810-381a-4c63-8d0f-7f01e289b664",
        "errors": [
            {
                "code": "40790101",
                "description": "Missing or invalid device identifier"
            }
        ]
    }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>