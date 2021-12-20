<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Get sitemap - API Specification

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
    <td>05 Oct 2021</td>
    <td>Tulaja Nandewar</td>
    <td>Draft Version</td>
  </tr>
  <tr>
    <td>2</td>
    <td> Oct 2021</td>
    <td>Manogar Subramani</td>
    <td>Initial review completed</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: GET

```
https://<server>/sitemap/source/feed/{type}
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

#### Path Parameter

<table width="100%">
  <tr>
    <th width='20%'>Name</th>
    <th>Type</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>type</td>
    <td>String</td>
    <td>Required</td>
    <td>type of the xml file. <br/>It may be "index", "static", "detail", "video" or "image".</td>
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
GET https://server/sitemap/source/feed/{type}
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
    <td>MIME type of the response payload - application/xml</td>
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
    <td>Loc</td>
    <td>String</td>
    <td>Required</td>
    <td>Location of the input identifier with the sitemap host in xml file for all type.</td>
  </tr>
   <tr>
    <td>lastmod</td>
    <td>String</td>
    <td>Required</td>
    <td>Last modified date of the input identifier in xml file for "detail", "index", "static" type.</td>
  </tr>
  <tr>
    <td>changefreq</td>
    <td>String</td>
    <td>Required</td>
    <td>Changed frquency of "static" and "detail" type identifier. <br/> Default vaule is : daily</td>
  </tr>
  <tr>
    <td>urlset</td>
    <td>String</td>
    <td>Required</td>
    <td>Represents a structure of image and video sitemap url set in xml file. </td>
  </tr>
  <tr>
    <td>image:loc</td>
    <td>String</td>
    <td>Required</td>
    <td>Represents a location of image element in image sitemap.</td>
  </tr>
  <tr>
    <td>image:title</td>
    <td>String</td>
    <td>Required</td>
    <td>Represents a detail information of image in image sitemap. <br/> Quality of movie, release year of the movie, language of the movie </td>
  </tr>
  <tr>
    <td>video:video</td>
    <td>String</td>
    <td>Required</td>
    <td>Represents a structure of video element in video sitemap. <br/> Which contain the thumbnail, title, description, family_friendly, uploader, player_location, <br/> subscription, duration, publishedDate, expirationDate, category, live, tag. </td>
  </tr>
  <tr>
    <td>video:thumbnail_loc</td>
    <td>String</td>
    <td>Required</td>
    <td>Formats video thumbnail url of the content. Which contain the imageResizerHost with <br/> content_id in url format</td>
  </tr>
  <tr>
    <td>video:title</td>
    <td>String</td>
    <td>Required</td>
    <td>Represents a detail information of video in video sitemap. <br/> Quality of movie, release year of the movie, language of the movie </td>
  </tr>
  <tr>
    <td>video:restriction relationship="allow"</td>
    <td>String</td>
    <td>Required</td>
    <td>Returns restriction definition of content by interpreting entitlement and denied countries definition. <br/> Example : AD AE AF AG AI AL AM AO AQ AR AS AT AU AW AX AZ BA BB BD <br/> BE BF BG BH BI BJ BL BM BN BO BQ </td>
  </tr>
  <tr>
    <td>video:family_friendly</td>
    <td>String</td>
    <td>Required</td>
    <td>Returns family friendly definition of content with Yes and No response. </td>
  </tr>
  <tr>
    <td>video:category</td>
    <td>String</td>
    <td>Required</td>
    <td>Returns formatted genre list of content. <br/> Example: Thriller | Romance | Drama | Dance Drama | Action | Romance Drama | Court Room Drama | Romance Comedy  </td>
  </tr>
  <tr>
    <td>video:live</td>
    <td>String</td>
    <td>Required</td>
    <td>Returns live status of content. </td>
  </tr>
  <tr>
    <td>video:tag</td>
    <td>String</td>
    <td>Required</td>
    <td>Returns sitemap tags of content. <br/> Example: anaganaga o athidi Telugu movie full movie, Telugu anaganaga o athidi, anaganaga o athidi Telugu movie full movie,<br/> anaganaga o athidi full movie, anaganaga o athidi  full movie Telugu, anaganaga o athidi full movie in Telugu 2020 hd.</td>
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

The following response is an example of successful read of the record for the input identifier of "detail"
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    <url>
        <loc>https://aha-web-ui.aha-stag.firstlight.ai/movie/anagana-o-athidhi</loc>
        <lastmod>2021-10-05</lastmod>
        <changefreq>daily</changefreq>
    </url>
    <url>
        <loc>https://aha-web-ui.aha-stag.firstlight.ai/movie/android-kattappa</loc>
        <lastmod>2021-10-05</lastmod>
        <changefreq>daily</changefreq>
    </url>
    "...": "..."
    "...": "..."
</urlset>
```

The following response is an example of successful read of the record for the input identifier of "index"
```xml
<?xml version="1.0" encoding="UTF-8"?>
<sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    <sitemap>
        <loc>https://sitemap.aha-stag.firstlight.ai/sitemap/sitemap-static.xml</loc>
        <lastmod>2021-10-05</lastmod>
    </sitemap>
    <sitemap>
        <loc>https://sitemap.aha-stag.firstlight.ai/sitemap/sitemap-detail.xml</loc>
        <lastmod>2021-10-05</lastmod>
    </sitemap>
    <sitemap>
        <loc>https://sitemap.aha-stag.firstlight.ai/sitemap/sitemap-video.xml</loc>
        <lastmod>2021-10-05</lastmod>
    </sitemap>
    <sitemap>
        <loc>https://sitemap.aha-stag.firstlight.ai/sitemap/sitemap-image.xml</loc>
        <lastmod>2021-10-05</lastmod>
    </sitemap>
</sitemapindex>
```

The following response is an example of successful read of the record for the input identifier of "static"
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    <url>
        <loc>https://aha-web-ui.aha-stag.firstlight.ai/all</loc>
        <lastmod>2021-10-05</lastmod>
        <changefreq>daily</changefreq>
    </url>
    <url>
        <loc>https://aha-web-ui.aha-stag.firstlight.ai/shows</loc>
        <lastmod>2021-10-05</lastmod>
        <changefreq>daily</changefreq>
    </url>
    "...": "..."
    "...": "..."
</urlset>    
```

The following response is an example of successful read of the record for the input identifier of "image"
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" xmlns:image="http://www.google.com/schemas/sitemap-image/1.1">
    <url>
        <loc>https://aha-web-ui.aha-stag.firstlight.ai/movie/anagana-o-athidhi</loc>
        <image:image>
            <image:loc>https://image-resizer-cloud.aha-stag.firstlight.ai/image/684F7053-A6D1-4431-8BCE-C4D548CCF805/0-16x9.jpg?width=1080</image:loc>
            <image:title>Watch anaganaga o athidi full movie Online in HD Quality. Film anaganaga o athidi is Release in the year.anaganaga o athidi Telugu full movie,anaganaga o athidi Telugu movie online</image:title>
        </image:image>
    </url>
    "...": "..."
    "...": "..."
</urlset>
```

The following response is an example of successful read of the record for the input identifier of "video"
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9" xmlns:video="http://www.google.com/schemas/sitemap-video/1.1">
    <url>
        <loc>https://aha-web-ui.aha-stag.firstlight.ai/movie/anagana-o-athidhi</loc>
        <video:video>
            <video:thumbnail_loc>https://image-resizer-cloud.aha-stag.firstlight.ai/image/684F7053-A6D1-4431-8BCE-C4D548CCF805/0-16x9.jpg?width=1080</video:thumbnail_loc>
            <video:title>Watch anaganaga o athidi full movie Online in HD Quality. Film anaganaga o athidi is Release in the year.anaganaga o athidi Telugu full movie,anaganaga o athidi Telugu movie online</video:title>
            <video:description></video:description>
            <video:restriction relationship="allow">AD AE AF AG AI AL AM AO AQ AR AS AT AU AW AX AZ BA BB BD BE BF BG BH BI BJ BL BM BN BO BQ BR BS BT BV BW BY BZ CA CC CD CF CG CH CI CK CL CM CN CO CR CU CV CW CX CY CZ DE DJ DK DM DO DZ EC EE EG EH ER ES ET FI FJ FK FM FO FR GA GB GD GE GF GG GH GI GL GM GN GP GQ GR GS GT GU GW GY HK HM HN HR HT HU ID IE IL IM IN IO IQ IR IS IT JE JM JO JP KE KG KH KI KM KN KP KR KW KY KZ LA LB LC LI LK LR LS LT LU LV LY MA MC MD ME MF MG MH MK ML MM MN MO MP MQ MR MS MT MU MV MW MX MY MZ NA NC NE NF NG NI NL NO NP NR NU NZ OM PA PE PF PG PH PK PL PM PN PR PS PT PW PY QA RE RO RS RU RW SA SB SC SD SE SG SH SI SJ SK SL SM SN SO SR SS ST SV SX SY SZ TC TD TF TG TH TJ TK TL TM TN TO TR TT TV TW TZ UA UG UM US UY UZ VA VC VE VG VI VN VU WF WS YE YT ZA ZM ZW</video:restriction>
            <video:family_friendly>yes</video:family_friendly>
            <video:uploader info="https://www.facebook.com/ahavideoIN">aha</video:uploader>
            <video:player_loc>https://vjs.zencdn.net/7.6.6/video.js</video:player_loc>
            <video:requires_subscription>yes</video:requires_subscription>
            <video:duration>5549</video:duration>
            <video:publication_date>2020-11-20</video:publication_date>
            <video:expiration_date>2020-07-09</video:expiration_date>
            <video:category>Thriller</video:category>
            <video:live>no</video:live>
            <video:tag>anaganaga o athidi Telugu full movie</video:tag>
            <video:tag>anaganaga o athidi Telugu movie</video:tag>
        </video:video>
    </url>
    "...": "..."
    "...": "..."
</urlset>

```
### Error Codes

<table width="100%">
  <tr>
    <th>Error Code</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>40860101</td>
    <td>Invalid or missing page number</td>
  </tr>
  <tr>
    <td>40860102</td>
    <td>Invalid or missing page size</td>
  </tr>
  <tr>
    <td>40860103</td>
    <td>No records found</td>
  </tr>
  <tr>
    <td>40860191</td>
    <td>Unknown failure</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>