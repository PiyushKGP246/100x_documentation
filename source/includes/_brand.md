# Brand
With this API you can create, update and list brands.

<b>Attributes</b>
<table>
<tbody>
<tr>
<td><b>id</b></td>
<td>Brand Id an integer.</td>
</tr>
<tr>
<td><b>description</b></td>
<td>Description of the brand.</td>
</tr>
<tr>
<td><b>image_url</b></td>
<td>URL of image.</td>
</tr>
<tr>
<td><b>category</b></td>
<td>Hopscotch defined Category to which brand is associated.</td>
</tr>
<tr>
<td><b>name</b></td>
<td>Brand name</td>
</tr>
<tr>
<td><b>short_name</b></td>
<td>Short name associated to brand</td>
</tr>
<tr>
<td><b>acronym</b></td>
<td>Brand acronym</td>
</tr>
</tbody>
</table>

## Create a Brand
> Example</br>
Lets say you have a brand named 'Uniqlo' of category "Apparel" with short name or acronym "UNQ". If you want the description to be "this is Uniqlo brand". You want "http://i.imgur.com/Q1a32kD.jpg" as main image of brand. Assume your access_token is "an_example_access_token" </br></br>
description = this is Uniqlo brand </br>
image_url = http://i.imgur.com/Q1a32kD.jpg </br>
category = Apparels </br>
name = Uniqlo </br>
short_name = UNQ </br>
acronym = UNQ </br>

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/brand/add -d "image_url=http://i.imgur.com/Q1a32kD.jpg&name=Uniqlo&description=this is Uniqlo brand&category=Apparels&short_name=UNQ&acronym=UNQ&access_token=an_example_access_token"
```

> Example Response

```json
{
    'message' : '',
    'code' : 0,
    'data' : 
    	{ 
    		"brand_id" : 101010
        }
}
```

Use below endpoint to create a new brand. </br>

<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/brand/add

<b>Parameters</b>
<table>
<tbody>
<tr>
<td><b>id</b></td>
<td>Brand Id an integer.</td>
</tr>
<tr>
<td><b>description</b></td>
<td>Description of the brand.</td>
</tr>
<tr>
<td><b>image_url</b></td>
<td>URL of image.</td>
</tr>
<tr>
<td><b>category</b></td>
<td>Hopscotch defined Category to which brand is associated.</td>
</tr>
<tr>
<td><b>name</b></td>
<td>Brand name</td>
</tr>
<tr>
<td><b>short_name</b></td>
<td>Short name associated to brand</td>
</tr>
<tr>
<td><b>acronym</b></td>
<td>Brand acronym</td>
</tr>
</tbody>
</table>

<b>Returns</b> </br>
Upon success, a brand will be created and brand_id(Hopscotch identifier) will be returned in the response.

## Update a Brand
> Example</br>
Assume your access token is "an_example_access_token" . If you had a brand with id 101010 and you wanted to change the short_name to "UNL", update the description to "This is an amazing brand." your parameters would be: </br></br>
id = 101010 </br>
short_name = Uniqlo </br>
description = This is an amazing brand. </br>
access_token = an_example_access_token </br>
If you did not want to update the description, you would omit that parameter from your API call.

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/brand/update -d "id=101010&short_name=UNL&description=This is an amazing brand.&access_token=an_example_access_token"
```

> Example Response

```json
{
    'code': 0,
    'data': {},
    'message': ''
}
```

Updates the specified brand with the parameters passed in the request. Any attribute not provided will be left unchanged. For example, if you pass the name parameter we will update the name of the brand and leave everything else unchanged.</br>

<b>HTTP Request Type: POST</b>

<b>Definition</b></br>
POST https://merchant.hopscotch.in/api/brand/update

<b>Parameters</b>
<table>
<tbody>
<tr>
<td><b>id</b></td>
<td>Brand Id an integer.</td>
</tr>
<tr>
<td><b>description</b></td>
<td>Description of the brand.</td>
</tr>
<tr>
<td><b>image_url</b></td>
<td>URL of image.</td>
</tr>
<tr>
<td><b>category</b></td>
<td>Hopscotch defined Category to which brand is associated.</td>
</tr>
<tr>
<td><b>name</b></td>
<td>Brand name</td>
</tr>
<tr>
<td><b>short_name</b></td>
<td>Short name associated to brand</td>
</tr>
<tr>
<td><b>acronym</b></td>
<td>Brand acronym</td>
</tr>
</tbody>
</table>

<b>Returns</b></br>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## List Brands
> Example</br>
Assume your access token is "an_example_access_token". If you would like to view your brands in groups of 2 and you would like to see the 10th group your parameters would be: </br></br>
start = 20 </br>
limit = 2 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl "https://merchant.hopscotch.in/api/brand/multi-get?limit=2&start=20&access_token=an_example_access_token"
```

> Example Response

```json
{
	'code': 0,
	'data': {
			'brands' : [
			{
				'description': 'this is Uniqlo brand',
				'image_url': 'http://i.imgur.com/Q1a32kD.jpg',
				'category': 'Apparels',
				'name': 'Uniqlo',
				'short_name': 'UNQ',
				'acronym': 'UNQ',
				'id': '101010'				
			}, {
				'description': 'this is Zara brand',
				'image_url': 'http://i.imgur.com/Q1a32kD.jpg',
				'category': 'Footwear',
				'name': 'Zara',
				'short_name': 'ZR',
				'acronym': 'ZR',
				'id': '101011'				
			}
		]
	},
	'message': '',
	'paging': 
		{
			'next': 'https://merchant.hopscotch.in/api/brand/multi-get?start=22&limit=2&access_token=an_example_access_token',
			'previous': 'https://merchant.hopscotch.in/api/brand/multi-get?start=18&limit=2&access_token=an_example_access_token'
		}
}	
```

Returns a list of all your brands currently on the Hopscotch platform. If you have a high number of brands the response will be paginated. The response will contain the URL for fetching the next page of brands.</br>

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/brand/multi-get

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>start</b>
		</td>
		<td>
			<b>optional</b> An offset into the list of returned items. Use 0 to start at the beginning. The API will return the requested number of items starting at this offset. Default to 0 if not supplied
		</td>
	</tr>
	<tr>
		<td>
			<b>limit</b>
		</td>
		<td>
			<b>optional</b> A limit on the number of brands that can be returned. Limit can range from 1 to 250 items and the default is 50
		</td>
	</tr>
	<tr>
		<td>
			<b>show_rejected</b>
		</td>
		<td>
			<b>optional</b> If specified to 'true', this API will return all brands including those inappropriate brands that were not approved.
		</td>
	</tr>
</table>

<b>Returns</b></br>
Response will contain a list of brand objects as well as a 'paging' field with paging options if needed.