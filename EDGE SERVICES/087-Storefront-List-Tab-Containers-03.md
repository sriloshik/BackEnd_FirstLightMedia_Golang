<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## List Storefront Tab Containers - API Specification

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
https://<server>/storefront/{sId}/{tId}/containers
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
    <td>Number that indicates the number of records to return in response. <br>Example: pageSize=25 indicates to return 25 records per request.<br>Default value: 10</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Example Request

```json
GET https://server/storefront/BCF5C97B-6E05-4891-AD4C-4F87FA39BD63/240C96C4-8DAD-46AA-AC4A-C916705F7A5E/containers?pageSize=2&pageNumber=1
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
    <td>List storefront tab containers response</td>
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
    "source": "087-03",
    "code": 0,
    "message": "Success",
    "system_time": 1633100286657,
    "start": 1,
    "rows": 2,
    "count": 12,
    "tracking_id": "e088e973-b031-48f6-8120-2dea20ce07e7"
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
      "con_tg": "regular",
      "con_ty": "regular",
      "ed_dt": "2025-05-25T18:29:00.000Z",
      "edit": false,
      "i": [
        {
          "count": 5,
          "cu": "https://data-store.aha-stag.firstlight.ai/content?mode=detail&st=published&ids=85D56847-BEB7-4C31-8F03-72FB55EE3FA6,CF86398B-F897-4DEA-B067-2AEC473A7309,AB4E98DA-CAA5-48C0-81A8-DB20084EE026,8F4F1DAD-0D2D-47E9-90F1-63B53C73D15A,B0955511-2C3E-4DC3-BDF4-3DDDCAF9C965",
          "priority": 1,
          "type": "manual"
        }
      ],
      "iar": "0-16x9",
      "id": "3259525B-15F0-4D5A-8156-CD2A3E7F4031",
      "lo": "banner",
      "lon": [
        {
          "lang": "en",
          "n": "HIGHLIGHTS"
        },
        {
          "lang": "te",
          "n": "హైలైట్స్"
        },
        {
          "lang": "ta",
          "n": "ஹைலைட்ஸ்"
        }
      ],
      "s": "regular",
      "st_dt": "2021-05-24T18:30:00.000Z",
      "stl": "regular",
      "urn": "urn:container"
    },
    "...": "...",
    "...": "...",
    "...": "..."
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
    <td>40870301</td>
    <td>Item not found</td>
  </tr>
  <tr>
    <td>40870302</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40870303</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40870305</td>
    <td>Invalid or missing policy attribute</td>
  </tr>
  <tr>
    <td>40870390</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40870391</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to storefront/tab not found:

```json
{
  "header": {
    "source": "087-03",
    "code": -1,
    "message": "Failure",
    "system_time": 1633099960617,
    "tracking_id": "e24af30f-b877-48dd-8b7f-bf0eff719202",
    "errors": [
      {
        "code": "40870301",
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
    "source": "087-03",
    "code": -1,
    "message": "Failure",
    "system_time": 1632227297215,
    "tracking_id": "6e271737-15b3-4611-84be-e82cce957fa6",
    "errors": [
      {
        "code": "40870302",
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
    "source": "087-03",
    "code": -1,
    "message": "Failure",
    "system_time": 1632227220267,
    "tracking_id": "bcc40a7c-a568-4862-a42d-516c7e66f929",
    "errors": [
      {
        "code": "40870303",
        "description": "Invalid or missing page size"
      }
    ]
  }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>