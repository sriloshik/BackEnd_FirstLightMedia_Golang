<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Browse Catalog(Retrieve Container Details of Storefront Tab) - API Specification

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
    <td>22 Sep 2021</td>
    <td>Tulaja Nandewar</td>
    <td>Draft Version</td>
  </tr>
  <tr>
    <td>2</td>
    <td>02 Oct 2021</td>
    <td>Manogar Subramani</td>
    <td>Initial review completed</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: GET

```
https://<server>/catalog/storefront/{sfid}/{tid}/containers
```

<div class="page"/>

#### Request Headers

<table width='100%'>
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
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

#### Path Parameters

<table width="100%">
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>sfid</td>
    <td>String</td>
    <td>Required</td>
    <td>Storefront ID</td>
  </tr>
  <tr>
    <td>tid</td>
    <td>String</td>
    <td>Required</td>
    <td>Tab ID to which the containers to be retrieved</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Example Request

```json
GET https://server/catalog/storefront/BCF5C97B-6E05-4891-AD4C-4F87FA39BD63/07FA689B-F2C1-4AA0-9BA8-6F60A67693F8/containers?containers?pageNumber=1&policy_evaluate=false&pageSize=25
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
    <td>Success or Failure response payload</td>
    <td>JSON</td>
    <td>Required</td>
    <td>Paginated list of container details</td>
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
    "source": "009-01",
    "code": 0,
    "message": "Success",
    "system_time": 1633094215457,
    "tracking_id": "3ec3dba6-5930-4de9-adb3-bda57c555623",
    "start": 1,
    "rows": 11,
    "count": 11
  },
  "data": [
    {
      "appliesif": {
        "acl": [
          "te"
        ],
        "dt": [
          "all"
        ],
        "reg": [
          "all"
        ],
        "sp": [
          "urn:package:te-monthly",
          "urn:package:te-quarterly",
          "urn:package:te-annual",
          "urn:package:combo",
          "urn:package:free"
        ]
      },
      "cd": [
        {
          "ad": "true",
          "adv": [
            "RO",
            "FG",
            "SH"
          ],
          "ao": "false",
          "aq": "Stereo",
          "ct": "2021-09-15T09:15:45Z",
          "cty": "movie",
          "dfs": [
            {
              "fn": "1631697309617-en-1-fwd-0.cmft",
              "fs": 418322,
              "ft": "encode_media_cmft",
              "q": ""
            }
            "...": "...",
            "...": "...",
            "...": "..."
          ]
        }
      ]
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
    <td>40090104</td>
    <td>Invalid or missing tab Id</td>
  </tr>
   <tr>
    <td>40090105</td>
    <td>Invalid or missing storefront Id</td>
  </tr>
  <tr>
    <td>40090190</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40090191</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure read due to storefront or tab not found:

``` json
{
  "header": {
    "source": "009-01",
    "code": -1,
    "message": "Failure",
    "system_time": 1633191741294,
    "tracking_id": "3a7daa80-f253-42d2-b295-2ae08a88944e",
    "errors": [
      {
        "code": "40870301",
        "description": "Item not found"
      }
    ]
  },
  "data": null
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>