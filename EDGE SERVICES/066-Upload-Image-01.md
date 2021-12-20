<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Upload Image - API Specification

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
    <td>    Sep 2021</td>
    <td>Senthilkumar Jeyarajan</td>
    <td>Reviewed and published</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: POST

```
https://<server>/image/upload/{selector}
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

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>


#### Example Request

```json
POST https://server/image/upload/{selector}
Authorization: Bearer <Access Token of IAM>
Content-Type: multipart/form-data


<!DOCTYPE html>
<html lang="en">   

<head>     
	<meta charset="UTF-8"  />     
	<meta name="viewport" content="width=device-width, initial-scale=1.0"  />     
	<meta http-equiv="X-UA-Compatible" content="ie=edge"  />     <title>Upload File</title>   </head>   

<body>     <form       enctype="multipart/form-data"
		      action="https://image-upload-service.sbox.edge.firstlight.ai/image/upload"       method="post"     >
		    <label for="UUID">UUID:</label>
		      <input type="text" name="UUID" /><br><br>     <label for="ImageType">Image Type:</label>
		    <input type="text" name="ImageType" /><br><br>     <label for="ImageAspectRatio">Image Aspect Ratio:</label>
		    <input type="text" name="ImageAspectRatio" /><br><br>     <input type="file" name="myFile" /><br><br>       <input type="submit" value="upload" />     </form>
		  </body>

</html> 

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
    "source": "MW-IMAGEUPLOAD-HTTP-01",
    "code": "0",
    "message": "Success",
    "systemtime": 1603441618012
  },
  "data": {
    "file_type": "image",
    "relative_uri": "images/BBB19022-97F4-4695-81A6-E95B0694E6CB/0-16X9",
    "blob_storage": "azure"
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
    <td>40660101</td>
    <td>Invalid Image Type</td>
  </tr>
  <tr>
    <td>40660102</td>
    <td>Missing or invalid height and/or width</td>
  </tr>
  <tr>
    <td>40660103</td>
    <td>Invalid image</td>
  </tr>
  <tr>
    <td>40660104</td>
    <td>Invalid or missing storage selector</td>
  </tr>
  <tr>
    <td>40660190</td>
    <td>System failure</td>
  </tr>
  <tr>
    <td>40660191</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to invalid image type,

```json
{
    "header": {
        "source": "066-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1632289770170,
        "tracking_id": "a58f1874-67c4-4a96-84ab-5c82fdba36ea",
        "errors": [
            {
                "code": "40660101",
                "description": "Invalid image type"
            }
        ]
    }
}
```

The following response is an example of failure due to invalid image type,

```json
{
    "header": {
        "source": "066-01",
        "code": -1,
        "message": "Failure",
        "system_time": 1632375393610,
        "tracking_id": "db179f61-0e66-4686-8089-27025fcc20fb",
        "errors": [
          {
                "code": "40660104",
                "description": "Invalid or missing storage selector"
            }
        ]
    }
}
      
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>