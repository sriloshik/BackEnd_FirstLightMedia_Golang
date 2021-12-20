<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Resize Image - API Specification

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
    <td>  Sep 2021</td>
    <td>Senthilkumar Jeyarajan</td>
    <td>Reviewed and published</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: GET

```
https://<server>/image/{id}/{name}
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

#### Request Body:

<table width="100%">
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
</table>

### 
<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET https://server/image/{id}/{name}
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

```
Content-Type: image/jpeg
<image>
```

### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>40420101</td>
    <td>Missing or invalid height</td>
  </tr>
  <tr>
    <td>40420102</td>
    <td>Missing or invalid width</td>
  </tr>
  <tr>
    <td>40420103</td>
    <td>Missing or invalid height and/or width</td>
  </tr>
  <tr>
    <td>40420104</td>
    <td>Invalid image format</td>
  </tr>
  <tr>
    <td>40420105</td>
    <td>Image not found</td>
  </tr>
  <tr>
    <td>40420106</td>
    <td>Invalid image</td>
  </tr>
  <tr>
    <td>40420107</td>
    <td>Invalid request</td>
  </tr>
  <tr>
    <td>40420108</td>
    <td>Invalid or missing storage selector</td>
  </tr>
  <tr>
    <td>40420190</td>
    <td>System failure</td>
  </tr>
  <tr>
    <td>40420191</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to image not found,

```json
{
    "header": {
        "source": "042-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1632289429940,
        "tracking_id": "90e2ceb9-7bdd-4125-aaca-1497e996c1ef",
        "errors": [
            {
                "code": "40420105",
                "description": "Image not found"
            }
        ]
    }
}
```

The following response is an example of failure due to invalid width,

```json
{
    "header": {
        "source": "042-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1632289531103,
        "tracking_id": "06e68f2d-a452-4043-b7ee-03d8c8c68787",
        "errors": [
            {
                "code": "40420102",
                "description": "Missing or invalid width"
            }
        ]
    }
}
```
The following response is an example of failure due to invalid input aspect ratio,

```json
{
    "header": {
        "source": "042-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1632306478413,
        "tracking_id": "e52ad4c2-e40f-448b-be6c-7630153a5738",
        "errors": [
            {
                "code": "40420103",
                "description": "Missing or invalid height and/or width"
            }
        ]
    }
}
```

The following response is an example of failure due to invalid image format,

```json
{
    "header": {
        "source": "042-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1632289770170,
        "tracking_id": "a58f1874-67c4-4a96-84ab-5c82fdba36ea",
        "errors": [
            {
                "code": "40420104",
                "description": "Invalid image format"
            }
        ]
    }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>