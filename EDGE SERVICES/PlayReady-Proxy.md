<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

### Acquire PlayReady License - API Specification

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
    <td>18 Sep 2021</td>
    <td>Senthilkumar Jeyarajan</td>
    <td>Created and published</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: POST

 ```
https://<host>/getlicense
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
    <td>Accept-Encoding</td>
    <td>String</td>
    <td>Optional</td>
    <td>HTTP header advertises which content encoding, usually a compression algorithm, the client is able to understand.</td>
  </tr>
  <tr>
    <td>Accept</td>
    <td>String</td>
    <td>Required</td>
    <td>HTTP header advertises which content types, expressed as MIME types, the client is able to understand.</td>
  </tr>
  <tr>
    <td>Content-Type</td>
    <td>String</td>
    <td>Required</td>
    <td>HTTP Header advertises the media type of the request body.</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Request Path Parameters

<table width='100%'>
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>service</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique identifier of the service.</td>
  </tr>
  <tr>
    <td>version</td>
    <td>String</td>
    <td>Required</td>
    <td>Version of the service configuration.</td>
  </tr>
  <tr>
    <td>kid</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique identifier of the content.</td>
  </tr>
  <tr>
    <td>ptoken</td>
    <td>String</td>
    <td>Required</td>
    <td>Time bound authorization token.</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Request Body

```
SOAP License challenge produced by the playready client player for the content being played.
```

<div class="page"/>

#### Example Request

```
POST https://<host>/getlicense?service=name&version=1.0&kid=37A4D0BB-CD2F-4491-95E4-1950B47A8773&ptoken=<value>
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
    <td>MIME type of the response payload</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Response Body

```
SOAP License envelope with the content encryption key understandable by the Playready client player. 
```

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

#### Error Samples

The following response is an exmaple of failure due to invalid service request parameter,

```json
{
    "header": {
        "source": "062-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1631937044178,
        "tracking_id": "9f26ce13-9873-47c4-960d-529e8275dbcd",
        "errors": [
            {
                "code": "40620101",
                "description": "Invalid or missing service"
            }
        ]
    }
}
```

The following response is an example of failure due to invalid ptoken request parameter,

```json
{
  "header": {
    "source": "062-01",
    "code": -1,
    "message": "Failure",
    "system_time": 1631936964795,
    "tracking_id": "c7b15894-e6d3-47cc-87a9-bc63e45fa7b9",
    "errors": [
      {
        "code": "40620103",
        "description": "Invalid ptoken"
      }
    ]
  }
}
```

<br/>

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>