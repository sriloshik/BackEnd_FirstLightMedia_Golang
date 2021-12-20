<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Get Config ById- API Specification

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
https://<server>/remote/config/lookup/{id}
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
  </table>

<hr style="height:1px;border-width:0;background-color:black">

#### Path Parameters

<table width='100%'>
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>id</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique identifier of the Config</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET https://server/remote/config/lookup/AABC4BFE-1640-4089-AB65-04988F12B6F1
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
    "source": "001-02",
    "code": 0,
    "message": "Success",
    "system_time": 1631859003132,
    "tracking_id": "61ce34f6-a68d-469a-b829-3690c4d6a92b"
  },
  "data": {
    "appliesif": [
      {
        "name": "type",
        "value": "appconfig"
      },
      {
        "name": "device",
        "value": "iosmobile"
      },
      {
        "name": "region",
        "value": "us"
      }
    ],
    "attrs": [
      {
        "key": "br_subtitle",
        "type": "String",
        "value": "en"
      },
      {
        "key": "audio_lang_default",
        "type": "String",
        "value": "en"
      }
    ],
    "ct": "2021-09-17T06:10:02Z",
    "d": "br_desc",
    "id": "90C781D3-5600-4520-9E9B-A48EE68F74DF",
    "key": "90C781D3-5600-4520-9E9B-A48EE68F74DF-1631859002",
    "n": "app_player_config_01",
    "st": "draft",
    "t": "config",
    "ut": "2021-09-17T06:10:02Z"
  }
}
```

<hr style="height:1px;border-width:0;background-color:black">

### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>40010501</td>
    <td>Invalid or missing config identifier</td>
  </tr>
  <tr>
    <td>40010502</td>
    <td>Config not exists</td>
  </tr>
  <tr>
    <td>40010503</td>
    <td>Invalid status</td>
  </tr>
  <tr>
    <td>40010590</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40010591</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to invalid config identifier,

```json
{
  "header": {
    "source": "001-05",
    "code": -1,
    "message": "Failure",
    "system_time": 1631868306804,
    "tracking_id": "b59cfb3f-5589-4399-b948-fa3d8dd7f30a",
    "errors": [
      {
        "code": "40010502",
        "description": "Config not exists"
      }
    ]
  }
}
```
<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>