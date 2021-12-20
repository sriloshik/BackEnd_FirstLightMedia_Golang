<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Browse Collection(Retrieve Container Details of Collection) - API Specification

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
https://<server>/catalog/collection/{cid}/containers
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
    <td>cid</td>
    <td>String</td>
    <td>Required</td>
    <td>CollectionID</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">


#### Example Request

```json
GET https://server/catalog/collection/49ECAB7D-2793-4F1C-8A79-096F69566A9E/containers
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
    "source": "009-02",
    "code": 0,
    "message": "Success",
    "system_time": 1633095145541,
    "tracking_id": "1d52e87d-adfd-4406-af7f-811001eaa419",
    "start": 1,
    "rows": 1,
    "count": 1
  },
  "data": [
    {
      "appliesif": {
        "acl": [
          "ta",
          "te"
        ],
        "dt": [
          "all"
        ],
        "reg": [
          "all"
        ],
        "sp": [
          "all"
        ]
      },
      "cd": [
        {
          "ad": "true",
          "ao": "false",
          "aq": "Stereo",
          "ct": "2021-09-01T17:14:32Z",
          "cty": "movie",
          "dfs": [
            {
              "fn": "7000.cmfv",
              "fs": 70000000,
              "ft": "video",
              "q": "high"
            },
            {
              "fn": "3000.cmfv",
              "fs": 30000000,
              "ft": "video",
              "q": "mid"
            },
            {
              "fn": "2000.cmfv",
              "fs": 20000000,
              "ft": "video",
              "q": "low"
            }
          ],
          "ed_dt": "2100-04-02T06:30:00Z",
          "ent": [
            {
              "con": "all",
              "det": "all",
              "dt": "all",
              "f_ed_dt": "2100-04-02T06:30:00Z",
              "f_st_dt": "2020-04-02T06:30:00Z",
              "sp": []
            }
          ],
          "ex_id": "ngk-mv-te-2019",
          "ia": [
            "0-3x1",
            "0-2x3",
            "0-16x9",
            "0-16x18",
            "0-9x16"
          ],
          "id": "EE780519-CE66-4E9B-9D3A-342B9648F75F",
          "key": "EE780519-CE66-4E9B-9D3A-342B9648F75F-1630516473412",
          "...": "...",
          "...": "...",
          "...": "..."
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
    <td>40090201</td>
    <td>Invalid or missing collection Id</td>
  </tr>
  <tr>
    <td>40090290</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40090291</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure read due to collection not found:

``` json
{
  "header": {
    "source": "087-01",
    "code": -1,
    "message": "Failure",
    "system_time": 1633191558577,
    "tracking_id": "4c20918a-65b1-4cde-85b0-83a7220c8301",
    "errors": [
      {
        "code": "40870101",
        "description": "Item not found"
      }
    ]
  }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>