<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## List Collection Containers - API Specification

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
https://<server>/storefront/{id}/containers
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
    <td>X-Tracking-Id</td>
    <td>String</td>
    <td>Optional</td>
    <td>Unique identifier to trace the HTTP request for errors. The service will auto-generate a new identifier to return in the response if this parameter was not received.<br/>Example - fb8812b9-b5f7-472d-9ab2-8e662253ca03</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Path Parameters

<table width="100%">
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
    <td>Collection id to which the containers to be retrieved</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Query Parameters

<table width="100%">
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>pageNumber</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Number that indicates the page to retrieve of the paginated list of items. <br>Example: pageNumber=2 indicates second page.<br>Default value: 1</td>
  </tr>
  <tr>
    <td>pageSize</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Number that indicates the number of records to return in response. <br>Example: pageSize=25 indicates to return 25 records per request.<br>Default value: 1</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Example Request

```json
GET https://server/storefront/49ECAB7D-2793-4F1C-8A79-096F69566A9E/containers?pageSize=2&pageNumber=1
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
    <td>List collection container response</td>
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
    "source": "087-04",
    "code": 0,
    "message": "Success",
    "system_time": 1633101853232,
    "start": 1,
    "rows": 1,
    "count": 1,
    "tracking_id": "e657075a-f33d-4f2d-b9c6-2c8c49867d25"
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
      "con_tg": "regular",
      "ed_dt": "2025-01-30T18:33:00.000Z",
      "edit": false,
      "i": [
        {
          "cu": "https://data-store.aha-stag.firstlight.ai/content/lookup?mode=detail&query=eyJmaWx0ZXIiOlt7ImZpZWxkIjoic3QiLCJ0ZXJtIjoicHVibGlzaGVkIiwib3BlcmF0b3IiOiJlcXVhbHMifSx7ImZpZWxkIjoiY3R5IiwidGVybSI6Im1vdmllLHNob3J0dmlkZW8sdHZzZXJpZXMsd2Vic2VyaWVzIiwib3BlcmF0b3IiOiJlcXVhbHMifSx7ImZpZWxkIjoibG9nLm4iLCJ0ZXJtIjoiQWN0aW9uIiwib3BlcmF0b3IiOiJlcXVhbHMifV0sIm1hdGNoIjoiQUxMIn0=",
          "priority": 4,
          "q": "{\"filter\":[{\"field\":\"st\",\"term\":\"published\",\"operator\":\"equals\"},{\"field\":\"cty\",\"term\":\"movie,shortvideo,tvseries,webseries\",\"operator\":\"equals\"},{\"field\":\"log.n\",\"term\":\"Action\",\"operator\":\"equals\"}],\"match\":\"ALL\"}",
          "type": "query"
        }
      ],
      "iar": "0-16x9",
      "id": "D3D5AFE7-CD0F-4525-918C-F3861B842B88",
      "...": "...",
      "...": "...",
      "...": "..."
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
    <td>40870401</td>
    <td>Item not found</td>
  </tr>
  <tr>
    <td>40870402</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40870403</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40870404</td>
    <td>Invalid or missing policy attribute</td>
  </tr>
  <tr>
    <td>40870490</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40870491</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to collection not found:

```json
{
  "header": {
    "source": "087-04",
    "code": -1,
    "message": "Failure",
    "system_time": 1633101029479,
    "tracking_id": "c2a4e568-ae6d-45dd-adfa-0bfae865e9bb",
    "errors": [
      {
        "code": "40870401",
        "description": "Item not found"
      }
    ]
  }
}
```

The following response is an example of failure due to invalid or missing page number:

```json
{
  "header": {
    "source": "087-04",
    "code": -1,
    "message": "Failure",
    "system_time": 1632228237201,
    "tracking_id": "2a998270-d0f2-4779-881c-cd793a400ac8",
    "errors": [
      {
        "code": "40870402",
        "description": "Invalid or missing page number"
      }
    ]
  }
}
```
The following response is an example of failure due to invalid or missing page size:

```json
{
  "header": {
    "source": "087-04",
    "code": -1,
    "message": "Failure",
    "system_time": 1632228261535,
    "tracking_id": "7b16fd49-94b5-45b1-a665-67b797380d51",
    "errors": [
      {
        "code": "40870403",
        "description": "Invalid or missing page size"
      }
    ]
  }
}
```
<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>