<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>

<hr style="height:1px;border-width:0;background-color:#f26524">

## Get Vod Source Feed - API Specification

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
    <td>Suriya Kumar</td>
    <td>Draft Version</td>
  </tr>
  <tr>
    <td>2</td>
    <td>Sep 2021</td>
    <td>Senthilkumar Jeyarajan</td>
    <td>Reviewed and published</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

### Request

#### HTTP Method: GET

```
https://<server>/cdf/source/feed/vod
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
    <td>pageNumber</td>
    <td>Number</td>
    <td>Optional</td>
    <td>Number that indicates the page to retrieve of the paginated list of items. <br>Example: pageNumber=2 indicates second page.<br>Default value: 1</td>
  </tr>
</table>

<hr style="height:1px;border-width:0;background-color:black">

<div class="page"/>

#### Example Request

```json
GET http(s)://server/cdf/source/feed/vod
Content-Type: application/json
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
    <td>Success or Failure response payload</td>
    <td>XML</td>
    <td>Required</td>
    <td>Amazon universal search feed xml data</td>
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

```` xml
<?xml version="1.0" encoding="UTF-8"?>
<Catalog
	xmlns="http://www.amazon.com/FireTv/2014-04-11/ingestion" version="FireTv-v1.11">
	<Partner>Aha</Partner>
	<Works>
		<Movie>
			<ID>FDE7885C</ID>
			<Title locale="en-US">Kanulu Kanulanu Dochayante</Title>
			<Offers>
				<FreeOffer>
					<Regions>
						<Country>CF</Country>
					</Regions>
					<WindowStart>2020-04-22T06:30:00Z</WindowStart>
					<WindowEnd>2025-04-22T06:30:00Z</WindowEnd>
					<LaunchDetails>
						<Quality>HD</Quality>
					</LaunchDetails>
				</FreeOffer>
			</Offers>
			<ReleaseYear>2020</ReleaseYear>
			<ShortDescription locale="en-US">Two clever engineers </ShortDescription>
			<Images>
				<Image>
					<Url>https://image-resizer-cloud.aha-stag.firstlight.ai/image/FDE7885C/0-16x9.jpg?width=1080</Url>
				</Image>
			</Images>
			<RuntimeMinutes>161</RuntimeMinutes>
			<Language>te</Language>
			<Genres>
				<Genre locale="en-US">Romance Thriller</Genre>
			</Genres>
		</Movie>
	</Works>
</Catalog>
````
<hr style="height:1px;border-width:0;background-color:#f26524">

<p align="center"><img src="https://cdn.shortpixel.ai/spai/w_378+q_lossy+ret_img+to_webp/https://firstlight.ai/wp-content/uploads/2021/03/300ppi-logotype-transparent.png" alt="Firstlight" height="30"/></p>
