<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Get Live Source Feed - API Specification

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
    <td>06 Oct 2021</td>
    <td>Tulaja Nandewar</td>
    <td>Draft Version</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: GET

```
https://<server>/gam/source/feed/live
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

<div class="page"/>

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
</table>

<hr style="height:1px;border-width:0;background-color:black">

#### Example Request

```json
GET https://server/gam/source/feed/live
```

```json
GET https://server/gam/source/feed/live?pageNumber=1
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
    <td>MIME type of the response payload - application/XML</td>
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
    <td>title</td>
    <td>String</td>
    <td>Required</td>
    <td>Title of the live channel and live item. </td>
  </tr>
  <tr>
    <td>dfpvideo:version</td>
    <td>String</td>
    <td>Required</td>
    <td>Indicates the current version of the MRSS spec that this feed uses. <br/> The value should be populated with an integer, and set once per feed. <br/> The only current valid value for this field is 2. </td>
  </tr>
  <tr>
    <td>atom:link</td>
    <td>String</td>
    <td>Required</td>
    <td>Identifies the feed's paging information. Ad Manager reads this element for two attributes: rel and href. <br/> rel indicates how the URL in the href attribute relates to the feed's result set. <br/> rel='next': Indicates that the href URL points to the next page of the feed's result set. If the feed contains an <atom:link> tag with rel='next', this indicates that there's another page of results. Otherwise, the current page is the last page in the result set. <br/> href specifies a URL that identifies the resource in the <atom:link> tag.</td>
  </tr>
  <tr>
    <td>item</td>
    <td>String</td>
    <td>Required</td>
    <td>Identifies a single video in the feed. An Ad Manager video feed may contain one or more <item> entries. Each of them are required to contain three elements for proper metadata ingestion: dfpvideo:contentId | dfpvideo:lastModifiedDate | title </td>
  </tr>
  <tr>
    <td>dfpvideo:contentId</td>
    <td>String</td>
    <td>Required</td>
    <td>Stored as the CMS content ID in Ad Manager. </td>
  </tr>
  <tr>
    <td>dfpvideo:lastModifiedDate</td>
    <td>String</td>
    <td>Required</td>
    <td>Indicates when any aspect of the video or its metadata was last modified. </td>
  </tr>
  <tr>
    <td>dfpvideo:keyvalues</td>
    <td>String</td>
    <td>Required</td>
    <td>Identifies any custom metadata for the video. <br/> It has the following attributes: key, value, and type. </td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

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

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss xmlns:atom="http://www.w3.org/2005/Atom" xmlns:media="http://search.yahoo.com/mrss/" xmlns:openSearch="http://a9.com/-/spec/opensearchrss/1.0/" xmlns:dfpvideo="http://api.google.com/dfpvideo" xmlns:tms="http://data.tmsapi.com/v1.1" version="2.0">
    <channel>
        <title>Rogers Sportsnet LIVE video source feed</title>
        <dfpvideo:version>2</dfpvideo:version>
        <atom:link rel="next" href="https://localhost:8080/gam/source/feed/live?pageNumber=2"></atom:link>
        <item>
            <pubDate>Tue, 05 Oct 2021 19:34:10 +0000</pubDate>
            <title>Free Preview Event Test </title>
            <dfpvideo:keyvalues key="title" value="Free Preview Event Test " type="string"></dfpvideo:keyvalues>
            <dfpvideo:keyvalues key="contenttype" value="sportliveevent" type="string"></dfpvideo:keyvalues>
            <dfpvideo:keyvalues key="sporttype" value="baseball" type="string"></dfpvideo:keyvalues>
            <dfpvideo:keyvalues key="sportleague" value="MLB" type="string"></dfpvideo:keyvalues>
            <dfpvideo:keyvalues key="hometeam" value="Pittsburgh Pirates" type="string"></dfpvideo:keyvalues>
            <dfpvideo:keyvalues key="awayteam" value="Chicago Cubs" type="string"></dfpvideo:keyvalues>
            <dfpvideo:keyvalues key="venue" value="PNC Park" type="string"></dfpvideo:keyvalues>
            <dfpvideo:keyvalues key="gameid" value="2296299" type="string"></dfpvideo:keyvalues>
            <dfpvideo:keyvalues key="eventstart" value="2021-09-29T14:35:00Z" type="string"></dfpvideo:keyvalues>
            <dfpvideo:keyvalues key="eventend" value="2021-09-30T00:50:14Z" type="string"></dfpvideo:keyvalues>
            <dfpvideo:keyvalues key="eventtype" value="regular" type="string"></dfpvideo:keyvalues>
            <media:thumbnail url="https://assets.sportsnet.ca/mlb_background_pit_chc_.png"></media:thumbnail>
            <dfpvideo:contentId>56A61817-3EEE-4566-9F26-AEBA2C5DFFC6</dfpvideo:contentId>
            <dfpvideo:lastModifiedDate>Tue, 05 Oct 2021 19:34:11 +0000</dfpvideo:lastModifiedDate>
        </item>
        "...": "...",
        "...": "..."
    </channel>
</rss>
```

<div class="page"/>

### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>40810201</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40810202</td>
    <td>No records found</td>
  </tr>
  <tr>
    <td>40810191</td>
    <td>Unknown failure</td>
  </tr>
</table>

<br/>

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>