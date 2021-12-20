<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Get Title Detail - API Specification

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
https://<server>/content/title/{titleId}
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
    <td>titleId</td>
    <td>String</td>
    <td>Required</td>
    <td>Unique identifier of the title. 
    This could be the content identifier of standalone title or series</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET https://server/content/title/{titleId}
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
    <td>Content/Title details</td>
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
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example OK Response

The following response is an example of successful retrieval of detail for title identifier:

```json

{
  "message": "success",
  "code": 0,
  "timestamp": 1631554574,
  "data": {
    "id": "4EA2065B-4F1B-4082-961A-97E00D30BC9F",
    "title": "Raja Vaaru Rani Gaaru",
    "originalTitle": "Raja Vaaru Rani Gaaru",
    "titleType": "movie",
    "description": "Description not available",
    "shortDescription": "What starts of as a classic tale of romance when Raja falls in love with Rani turns into a captivating adventure as the two try to work their way through time's tapestry and outlast the toils of love. Will fate even work in their favor?",
    "hrPosterUrl": "https://image-resizer-cloud.aha-stag.firstlight.ai/image/4EA2065B-4F1B-4082-961A-97E00D30BC9F/0-16x9.jpg?width=1280",
    "vrPosterUrl": "https://image-resizer-cloud.aha-stag.firstlight.ai/image/4EA2065B-4F1B-4082-961A-97E00D30BC9F/0-2x3.jpg?width=720",
    "releaseDate": "",
    "runtime": 7800,
    "resolution": 2,
    "pictureQuality": 0,
    "soundEffect": 0,
    "genres": [
      "Romance"
    ],
    "languages": [
      "Telugu"
    ],
    "regions": [
      "Telugu"
    ],
    "channels": [
      "aha-tv"
    ],
    "directors": [
      "Ravi Kiran Kola"
    ],
    "principalCast": [
      "Rajkumar Kasireddy",
      "Yazurved Gurram"
    ],
    "playingType": 0,
    "payType": 3,
    "isFinal": false,
    "age": 0,
    "deeplink": "https://www.aha.video/player/movie/raja-vaaru-rani-gaaru"
  }
}
```

The following response is an example of success response for show details retrieval:

```json

{
  "message": "success",
  "code": 0,
  "timestamp": 1631555019,
  "data": {
    "id": "EB6068D9-E65F-45AC-9069-B715FF27058E",
    "title": "Kothaporadu",
    "originalTitle": "Kothaporadu",
    "titleType": "series",
    "description": "Description not available",
    "shortDescription": "This story revolves around Raju, a care-free village guy who is new to the city. While his struggle seems to be never-ending, fate has a different plan in store for him. Watch Kothaporadu and know more about his journey.",
    "hrPosterUrl": "https://image-resizer-cloud.aha-stag.firstlight.ai/image/EB6068D9-E65F-45AC-9069-B715FF27058E/0-16x9.jpg?width=1280",
    "vrPosterUrl": "https://image-resizer-cloud.aha-stag.firstlight.ai/image/EB6068D9-E65F-45AC-9069-B715FF27058E/0-2x3.jpg?width=720",
    "releaseDate": "",
    "runtime": 0,
    "resolution": 0,
    "pictureQuality": 0,
    "soundEffect": 0,
    "genres": [],
    "languages": [
      "Telugu"
    ],
    "regions": [
      "Telugu"
    ],
    "channels": [
      "aha-tv"
    ],
    "directors": [],
    "principalCast": [
      "Anvesh Michael",
      "Sudhakar Reddy",
      "Raj Tirandas",
      "Sai Prasanna"
    ],
    "playingType": 0,
    "payType": 3,
    "isFinal": false,
    "age": 0,
    "seasons": [
      {
        "id": "BE8EC421-36DD-4D9D-82BE-5B586AD0F4C0",
        "showId": "EB6068D9-E65F-45AC-9069-B715FF27058E",
        "title": "Kothaporadu season 1",
        "seasonNumber": 1,
        "numEpisodes": 10,
        "episodes": [
          {
            "id": "73E59650-E123-419B-96CD-1F48B3EC7412",
            "showId": "EB6068D9-E65F-45AC-9069-B715FF27058E",
            "seasonId": "BE8EC421-36DD-4D9D-82BE-5B586AD0F4C0",
            "episodeNumber": 1,
            "title": "Kotlata",
            "description": "Description not available",
            "releaseDate": "",
            "downloadable": true,
            "playDuration": 1457,
            "previewUrl": "https://image-resizer-cloud.aha-stag.firstlight.ai/image/73E59650-E123-419B-96CD-1F48B3EC7412/0-16x9.jpg?width=1280",
            "soundEffect": 0,
            "deeplink": "https://www.aha.video/player/webepisode/kotha-poradu-kotlata-s1-e1"
          },
          "...": "...",
          "...": "...",
          "...": "..."
        ]
      }
    ]
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
    <td>1</td>
    <td>Invalid parameters</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Empty data</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Forbidden</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Error Samples

The following response is an example of failure read due to invalid request parameter:

```json
{
  "message": "failure",
  "code": 1,
  "timestamp": 1631553945
}
```
The following response is an example of failure read due to empty data:

```json
{
  "message": "failure",
  "code": 2,
  "timestamp": 1631553987
}
```

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>