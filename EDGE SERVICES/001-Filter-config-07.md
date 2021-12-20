<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Filter Config - API Specification

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
    <td>21 Aug 2021</td>
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

#### HTTP Method: GET/POST

```
https://<server>/remote/config/filter
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

#### Request query parameters

<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Required / Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>query</td>
    <td>String</td>
    <td>Optional(FOR POST)</td>
    <td>Filer Query</td>
  </tr>
  <tr>
    <td>pageNumber</td>
    <td>String</td>
    <td>Optional</td>
    <td>Page number</td>
  </tr>
    <tr>
    <td>pageSize</td>
    <td>String</td>
    <td>Optional</td>
    <td>Page size</td>
  </tr>
   <tr>
    <td>sortBy</td>
    <td>String</td>
    <td>Optional</td>
    <td>Sort field</td>
  </tr>
   <tr>
    <td>sortOrder</td>
    <td>String</td>
    <td>Optional</td>
    <td>Sort order - asc | desc</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET https://server/remote/config/filter?query=eyJmaWx0ZXIiOlt7ImZpZWxkIjoiQ29uZGl0aW9ucyIsIm9wZXJhdG9yIjoiY29udGFpbnMiLCJ0ZXJtIjoidXMifV19
Authorization: Bearer <Access Token of IAM>

```

```json 
POST https://server//remote/config/filter?pageNumber=1&pageSize=10
Authorization: Bearer <Access Token of IAM>
Content-Type: application/json
{
  "filter": [
    {
      "field": "n",
      "term": "test",
      "operator": "equals"
    },
    {
      "field": "t",
      "term": "config",
      "operator": "equals"
    },
    {
      "field": "st",
      "term": "published",
      "operator": "equals"
    }
  ]
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

```json
{
  "header": {
    "source": "001-07",
    "code": 0,
    "message": "Success",
    "system_time": 1598438428185,
    "start": 1,
    "rows": 1,
    "count": 1,
    "tracking_id": "4c0be91a-161c-4f69-9fbf-dc440ae02d77"
  },
  "data": [
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
      "ct": "2020-08-26T08:03:08Z",
      "d": "br_desc",
      "id": "05A36E16-5BE1-4050-9E4E-6F19A11F61ED",
      "key": "05A36E16-5BE1-4050-9E4E-6F19A11F61ED-1598428988",
      "n": "app_player_config_6",
      "st": "draft",
      "t": "config",
      "ut": "2020-08-26T08:03:08Z"
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
    <td>40010701</td>
    <td>Invalid or missing query</td>
  </tr>
  <tr>
    <td>40010702</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40010703</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40010704</td>
    <td>Invalid or missing sort by</td>
  </tr>
  <tr>
    <td>40010705</td>
    <td>Invalid or missing sort order</td>
  </tr>
  <tr>
    <td>40010706</td>
    <td>No records found</td>
  </tr>
  <tr>
    <td>40010790</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40010791</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to invalid query,

```json
{
  "header": {
    "source": "001-07",
    "code": -1,
    "message": "Failure",
    "system_time": 1632220847215,
    "tracking_id": "561082e6-61b7-4aec-981b-d5768f7a44ab",
    "errors": [
      {
        "code": "40010701",
        "description": "Invalid or missing query"
      }
    ]
  }
}
```
The following response is an example of failure due to invalid page number,

```json
{
  "header": {
    "source": "001-07",
    "code": -1,
    "message": "Failure",
    "system_time": 1632221162471,
    "tracking_id": "e05f71ec-ecd2-4161-880b-1a0b65a30edd",
    "errors": [
      {
        "code": "40010702",
        "description": "Invalid or missing page number"
      }
    ]
  }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>