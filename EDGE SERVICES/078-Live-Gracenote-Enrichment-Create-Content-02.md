<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Live Gracenote Enrichment - Create Content - API Specification

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
    <td>Santhosh Prabakaran</td>
    <td>Draft Version</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: POST

```
https://<server>/content/urn/resource/{caty}/{cty}
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

#### Request Path Parameters

<table width='100%'>
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>cty</td>
    <td>String</td>
    <td>Required</td>
    <td>Content type. <br/>Allowed values are; sportliveevent</td>
  </tr>
  <tr>
    <td>caty</td>
    <td>String</td>
    <td>Required</td>
    <td>Catalog type. <br/>Allowed values are; catalog</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
POST https://server/content/urn/resource/catalog/sportliveevent
Authorization: Bearer <Access Token of IAM>
Content-Type: application/json

{
    "urn": "urn:resource:catalog:sportliveevent",
    "id": "48019B13-F9E6-4694-904E-D805EEDEC033",
    "cty": "sportliveevent",
    "st": "published",
    "ep":[
        {
            "n": "gracenote",
            "id": "EP029941835361"
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

``` json
{
  "header": {
    "source": "078-02",
    "code": 0,
    "message": "Success",
    "system_time": 1633074450510,
    "tracking_id": "4242b667-7aa3-4ebc-90a0-ad346cf22c86"
  },
  "data": {
    "ct": "2021-10-01T07:47:29Z",
    "cty": "sportliveevent",
    "ep": [
      {
        "id": "EP029941835361",
        "n": "gracenote"
      }
    ],
    "id": "48019B13-F9E6-4694-904E-D805EEDEC033",
    "key": "48019B13-F9E6-4694-904E-D805EEDEC033-1633074449",
    "...": "...",
    "...": "..."
  }
}
```

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

### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>40780201</td>
    <td>Invalid or missing content type</td>
  </tr>
  <tr>
    <td>40780202</td>
    <td>Item not found</td>
  </tr>
  <tr>
    <td>40780290</td>
    <td>Subsystem failure</td>
  </tr>
  <tr>
    <td>40780291</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure due to invalid content type,

```json
{
    "header": {
        "source": "078-02",
        "code": -1,
        "message": "Failure",
        "system_time": 1632212190648,
        "tracking_id": "381c46b0-92da-4324-bd67-38d9e96a4704",
        "errors": [
            {
                "code": "40780201",
                "description": "Invalid or missing content type"
            }
        ]
    }
}
```

The following response is an example of failure due to item not found,

```json
{
    "header": {
        "source": "078-02",
        "code": -1,
        "message": "Failure",
        "system_time": 1632212190648,
        "tracking_id": "381c46b0-92da-4324-bd67-38d9e96a4704",
        "errors": [
            {
                "code": "40780202",
                "description": "Item not found"
            }
        ]
    }
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>