<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Search Storefront - API Specification

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
https://<server>/storefront/search
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

#### Query Parameters

<table width="100%">
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>term</td>
    <td>String</td>
    <td>Required</td>
    <td>Name of the container.</td>
  </tr>
  <tr>
    <td>ty</td>
    <td>String</td>
    <td>Optional</td>
    <td>Storefront type.</td>
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
    <td>Number that indicates the number of records to return in response. <br>Example: pageSize=25 indicates to return 25 records per request.<br>Default value: 10</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Example Request

```json
GET https://server/storefront/search?term=searchTerm&ty=storefrontType?pageSize=2&pageNumber=1
Example: searchTerm: action and storefrontType: Storefront
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
    <td>Search storefront response</td>
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
    "source": "087-05",
    "code": 0,
    "message": "Success",
    "system_time": 1633168188600,
    "start": 1,
    "rows": 1,
    "count": 1,
    "tracking_id": "1b330573-0531-40de-be24-8ffee5cc0cdc"
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
      "bgc": "#000000",
      "c": [
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
    <td>40870501</td>
    <td>Invalid or missing search term</td>
  </tr>
  <tr>
    <td>40870502</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40870503</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40870504</td>
    <td>Item not found</td>
  </tr>
   <tr>
    <td>40870505</td>
    <td>Invalid or missing policy attribute</td>
  </tr>
  <tr>
    <td>40870590</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40870591</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to Invalid or missing search term:

```json
{
  "header": {
    "source": "087-05",
    "code": -1,
    "message": "Failure",
    "system_time": 1632229614362,
    "tracking_id": "9a64497f-1502-4006-9321-d5240924ce78",
    "errors": [
      {
        "code": "40870501",
        "description": "Invalid or missing search term"
      }
    ]
  }
}
```

The following response is an example of failure due to invalid or missing page number:

```json
{
  "header": {
    "source": "087-05",
    "code": -1,
    "message": "Failure",
    "system_time": 1632230315353,
    "tracking_id": "0830677e-28da-48f1-b2a1-b39ad3e82ea6",
    "errors": [
      {
        "code": "40870502",
        "description": "Invalid or missing page number"
      }
    ]
  }
}
```

The following response is an example of failure due to item not found:

```json
{
  "header": {
    "source": "087-05",
    "code": -1,
    "message": "Failure",
    "system_time": 1633102282225,
    "tracking_id": "de27220b-3997-48f8-beed-a752c6f287f0",
    "errors": [
      {
        "code": "40870504",
        "description": "Item not found"
      }
    ]
  }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>