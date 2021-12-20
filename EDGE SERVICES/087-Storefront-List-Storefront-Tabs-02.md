<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## List Storefront Tabs - API Specification

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
https://<server>/storefront/{id}/tabs
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
    <td>Storefront id to which the tabs to be retrieved</td>
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
    <td>Number that indicates the number of records to return in response. <br>Example: pageSize=25 indicates to return 25 records per request.<br>Default value: 10 </td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Example Request

```json
GET https://server/storefront/BCF5C97B-6E05-4891-AD4C-4F87FA39BD63/tabs?pageSize=3&pageNumber=1
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
    <td>List storefront tab response</td>
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
    "source": "087-02",
    "code": 0,
    "message": "Success",
    "system_time": 1633099551708,
    "start": 1,
    "rows": 3,
    "count": 4,
    "tracking_id": "c56dc733-6ea3-4c5c-bc57-5bec40ebe27a"
  },
  "data": [
    {
      "id": "07FA689B-F2C1-4AA0-9BA8-6F60A67693F8",
      "lon": [
        {
          "lang": "en",
          "n": "All"
        },
        {
          "lang": "te",
          "n": "అన్నీ"
        },
        {
          "lang": "ta",
          "n": "அனைத்தும்"
        }
      ]
    },
    {
      "id": "85EFFE80-F71D-4A78-804D-90477969FDC5",
      "lon": [
        {
          "lang": "en",
          "n": "Movies"
        },
        {
          "lang": "te",
          "n": "సినిమాలు"
        },
        {
          "lang": "ta",
          "n": "திரைப்படங்கள்"
        }
      ]
    },
    {
      "id": "240C96C4-8DAD-46AA-AC4A-C916705F7A5E",
      "lon": [
        {
          "lang": "en",
          "n": "Shows"
        },
        {
          "lang": "te",
          "n": "ప్రదర్శనలు"
        },
        {
          "lang": "ta",
          "n": "நிகழ்ச்சிகள்"
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
    <td>40870201</td>
    <td>Item not found</td>
  </tr>
  <tr>
    <td>40870202</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40870203</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40870204</td>
    <td>Invalid or missing policy attribute</td>
  </tr>
  <tr>
    <td>40870290</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40870291</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to storefront not found:

```json
{
  "header": {
    "source": "087-02",
    "code": -1,
    "message": "Failure",
    "system_time": 1633097900536,
    "tracking_id": "7fb47c0f-7e63-4108-bcd9-fec5b28fa7c5",
    "errors": [
      {
        "code": "40870201",
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
    "source": "087-02",
    "code": -1,
    "message": "Failure",
    "system_time": 1632220951158,
    "tracking_id": "ab3fbefa-a641-4213-984f-478d417f6a42",
    "errors": [
      {
        "code": "40870202",
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
    "source": "087-02",
    "code": -1,
    "message": "Failure",
    "system_time": 1632220845703,
    "tracking_id": "9448001d-5f76-4f4f-a089-fd0dc4ce53c0",
    "errors": [
      {
        "code": "40870203",
        "description": "Invalid or missing page size"
      }
    ]
  }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>