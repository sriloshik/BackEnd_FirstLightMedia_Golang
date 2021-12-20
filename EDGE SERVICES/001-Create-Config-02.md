<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Create Config - API Specification

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
    <td>30   Sep 2021</td>
    <td>Yashwanth Lakshmidhar</td>
    <td>Initial Review</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: POST

```
https://<server>/remote/config/create
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
    <td>Publication Status
        <br/>Allowed values : published, draft, archived</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
POST https://server/remote/config/create
Authorization: Bearer <Access Token of IAM>
Content-Type: application/json

{
  "appliesif": [
    {
      "name": "device",
      "value": "iosmobile"
    },
    {
      "name": "region",
      "value": "us"
    },
    {
      "name": "type",
      "value": "appconfig"
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
  "d": "br_desc",
  "n": "app_player_config_01",
  "st": "draft",
  "t": "config"
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

``` json
{
  "header": {
    "source": "001-02",
    "code": 0,
    "message": "Success",
    "system_time": 1598435569492,
    "tracking_id": "73e7df1b-cf00-49e1-81b1-fcdb5afea0a8"
  },
  "data": {
    "appliesif": [
      {
        "name": "device",
        "value": "iosmobile"
      },
      {
        "name": "region",
        "value": "br"
      },
      {
        "name": "type",
        "value": "appconfig"
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
    "ct": "2020-08-26T09:52:49Z",
    "d": "br_desc",
    "id": "CF4819BC-F9FD-415E-B045-E03A0B21DE2C",
    "key": "CF4819BC-F9FD-415E-B045-E03A0B21DE2C-1598435569",
    "n": "app_player_config_6",
    "st": "draft",
    "t": "config",
    "ut": "2020-08-26T09:52:49Z"
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
    <td>40010201</td>
    <td>Invalid status</td>
  </tr>
    <td>40010290</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40010291</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to invalid status provided,

```json
{
  "header": {
    "source": "001-02",
    "code": -1,
    "message": "Failure",
    "system_time": 1631859239729,
    "tracking_id": "d6074d8f-6d76-4bdd-a428-ef6dd25f8ca7",
    "errors": [
      {
        "code": "40010201",
        "description": "Invalid status"
      }
    ]
  }
}
```
<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>