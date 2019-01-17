# Product
The product entity represents an item that is for sale on Hopscotch. Each product can have multiple variations comprised of different sizes. Each product has at least one product variation. Product variations, not products, are purchased by users. Each product contains multiple related SKUs.

With this API you can create and update products. You can also retrieve details about specific product or page through all your products.

<!-- <b>Attributes</b> -->

## Create a Product
> Example</br>
Lets say you had product named "red shoe" with a SKU of red-shoe-11 and shipping of $10.00. If you want the description to be "this is a cool shoe". You want "http://i.imgur.com/Q1a32kD.jpg" to be the main image for your product and have additional imge "http://i.imgur.com/Cxagv.jpg" and "http://i.imgur.com/LuPSxBM.jpg". Assume your access token is "an_example_access_token" </br></br>
name = red shoe </br>
parent_sku = red-shoe </br>
sku = red-shoe-11 </br>
shipping = 10 </br>
description = this is a cool shoe </br>
main_image = http://i.imgur.com/Q1a32kD.jpg </br>
extra_images=http://i.imgur.com/Cxagv.jpg|http://i.imgur.com/Cxagv.jpg </br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/product/add -d "main_image=http://i.imgur.com/Q1a32kD.jpg&name=red shoe&description=this is a cool shoe&sku=red-shoe-11&shipping=10&extra_images=http://i.imgur.com/Q1a32kD.jpg|http://i.imgur.com/Cxagv.jpg&access_token=an_example_access_token"

```

> Example Response

```json
{
    'message' : '',
    'code' : 0,
    'data' : 
    	{ 
    		"product_id" : 101010
        }
}
```

Use below endpoint to create a new product. </br>

<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/product/add

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>name</b>
		</td>
		<td>
			The name which you have given the product, example: 'Blue Shoe'	
		</td>
	</tr>
	<tr>
		<td>
			<b>description</b>
		</td>
		<td>
			A blurb of text uploaded as the description to the product
		</td>
	</tr>
	<tr>
		<td>
			<b>declared_name</b>
		</td>
		<td>
			<b>optional</b> Product name for logistics declaration </br>
			Acceptable: Repair Tools Kit Set </br>
			Acceptable: Rings </br>
			Unacceptable: !Rings </br>
			Unacceptable: T </br>
			Unacceptable: Good 衬衫 </br>
			Unacceptable: Name that is longer than 200 characters
		</td>
	</tr>
	<tr>
		<td>
			<b>declared_local_name</b>
		</td>
		<td>
			<b>optional</b> Product name written in local language for logistics declaration </br>
			Acceptable: 棉质外套 </br>
			Unacceptable: !棉质外套 </br>
			Unacceptable: 棉 </br>
			Unacceptable: Name that is longer than 200 characters
		</td>
	</tr>
	<tr>
		<td>
			<b>sku</b>
		</td>
		<td>
			The unique identifier that your system uses to recognize this product
		</td>
	</tr>
	<tr>
		<td>
			<b>pieces</b>
		</td>
		<td>
			<b>optional</b> The amount of pieces associated with this item </br>
			Acceptable: 2 </br>
			Acceptable: 1 </br>
			Unacceptable: -1
		</td>
	</tr>
	<tr>
		<td>
			<b>color</b>
		</td>
		<td>
			<b>optional</b> The color of the product. Example: red, blue, green
		</td>
	</tr>
	<tr>
		<td>
			<b>shipping</b>
		</td>
		<td>
			<b>optional</b> The shipping of the variation when the user purchases one, max 1000
		</td>
	</tr>
	<tr>
		<td>
			<b>main_image</b>
		</td>
		<td>
			URL of the main image of the product
		</td>
	</tr>
	<tr>
		<td>
			<b>extra_images</b>
		</td>
		<td>
			URL of all extra images of the product, separated by the character '|'
		</td>
	</tr>
	<tr>
		<td>
			<b>landing_page_url</b>
		</td>
		<td>
			URL on your website containing the product details
		</td>
	</tr>
	<tr>
		<td>
			<b>upc</b>
		</td>
		<td>
			12-digit Universal Product Codes (UPC)-contains no letters or other characters
		</td>
	</tr>
	<tr>
		<td>
			<b>hscode</b>
		</td>
		<td>
			<b>optional</b> Harmonization System Code used for custom declaration. </br>
			Acceptable: 33021010.00 </br>
			Acceptable: 6403.20 </br>
			Unacceptable: 2 </br>
			Unacceptable: a
		</td>
	</tr>
	<tr>
		<td>
			<b>category_name </b>
		</td>
		<td>
			Name of the category this prouct belongs to, category structure as per Hopscotch structure. 
		</td>
	</tr>
	<tr>
		<td>
			<b>origin_country</b>
		</td>
		<td>
			<b>optional</b> country where product is manufactured. Country code should follow ISO 3166 Alpha-2 code. Example:CN, US </br>
			Acceptable: CN </br>
			Acceptable: US </br>
			Unacceptable: China
		</td>
	</tr>
	<tr>
		<td>
			<b>has_powder</b>
		</td>
		<td>
			<b>optional</b> Whether product contains powder. Example: true, false. </br>
			Acceptable: Yes </br>
			Acceptable: No </br>
			Unacceptable: 0
		</td>
	</tr>
	<tr>
		<td>
			<b>has_liquid</b>
		</td>
		<td>
			<b>optional</b> Whether product contains liquid. Example: true, false. </br>
			Acceptable: Yes </br>
			Acceptable: No </br>
			Unacceptable: 0
		</td>
	</tr>
	<tr>
		<td>
			<b>has_battery</b>
		</td>
		<td>
			<b>optional</b> Whether product contains battery. Example: true, false. </br>
			Acceptable: Yes </br>
			Acceptable: No </br>
			Unacceptable: 0
		</td>
	</tr>
	<tr>
		<td>
			<b>has_metal</b>
		</td>
		<td>
			<b>optional</b> Whether product contains metal. Example: true, false. </br>
			Acceptable: Yes </br>
			Acceptable: No </br>
			Unacceptable: 0
		</td>
	</tr>
	<tr>
		<td>
			<b>unique_code</b>
		</td>
		<td>
			<b>optional,</b> any unique code used as the identifier for an individual item. 
		</td>
	</tr>
	<tr>
		<td>
			<b>gender</b>
		</td>
		<td>
			<b>optional,</b> mention if the item is for male, female or unisex.
		</td>
	</tr>
	<tr>
		<td>
			<b>manufacturing year</b>
		</td>
		<td>
			<b>optional,</b> year of manufacture in 20XX format. 
		</td>
	</tr>
	<tr>
		<td>
			<b>parent_sku</b>
		</td>
		<td>
			<b>optional</b> When defining a variant of a product we must know which product to attach the variation to. parent_sku is the unique id of the product that you can use later when using the add product variation API.
		</td>
	</tr>
	<tr>
		<td>
			<b>brand</b>
		</td>
		<td>
			<b>optional</b> Brand or manufacturer of your product
		</td>
	</tr>
	<tr>
		<td>
			<b>season</b>
		</td>
		<td>
			<b>optional,</b> season can be all, summer, spring, fall, winter or monsoon
		</td>
	</tr>
	<tr>
		<td>
			<b>quantity_per_case_pack</b>
		</td>
		<td>
			If the number of items in a single product is more than 1 </br>
			Acceptable: 12 </br>
			Unacceptable: 2.12 </br>
			Unacceptable: a
		</td>
	</tr>
</table>

<b>Returns</b> </br>
Upon success, a product will be created and product_id(Hopscotch identifier) will be returned in the response.

## Update a Product
> Example</br>
Assume your access token is "an_example_access_token" . If you had a product with id 10101 and you wanted to change the name to "Awesome shoe", update the description to "This shoe is the best on Hopscotch" your parameters would be: </br></br>
id = 10101 </br>
name = Awesome shoe </br>
description = This shoe is the best on Hopscotch </br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/product/update -d "id=10101&name=Awesome shoe&description=This shoe is the best on Wish&access_token=an_example_access_token"
```

> Example Response

```json
{
    'code': 0,
    'data': {},
    'message': ''
}
```

Updates the specified product with the parameters passed in the request. Any attribute not provided will be left unchanged. For example, if you pass the name parameter we will update the name of the product and leave everything else unchanged.</br>

This request can only update attributes specific to products and cannot be used to update anything to do with the product variations of a product.</br>

<b>HTTP Request Type: POST</b>

<b>Definition</b></br>
POST https://merchant.hopscotch.in/api/product/update

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>id</b>
		</td>
		<td>
			Must provide either id or parent_sku Hopscotch's unique identifier for the product you would like to update
		</td>
	</tr>
	<tr>
		<td>
			<b>parent_sku</b>
		</td>
		<td>
			Must provide either id or parent_sku The parent sku for the product you would like to update
		</td>
	</tr>
	<tr>
		<td>
			<b>name</b>
		</td>
		<td>
			<b>optional</b> Name of the product as shown to users
		</td>
	</tr>
	<tr>
		<td>
			<b>description</b>
		</td>
		<td>
			<b>optional</b> Description of the product. If you want a new line use "\n".
		</td>
	</tr>
	<tr>
		<td>
			<b>upc</b>
		</td>
		<td>
			<b>optional</b> 12-digit Universal Product Codes (UPC)-contains no letters or other characters
		</td>
	</tr>
	<tr>
		<td>
			<b>main_image</b>
		</td>
		<td>
			<b>optional</b> URL of a photo of your product. Link directly to the image, not the page where it is located. We accept JPEG, PNG or GIF format. Images should be at least 100 x 100 pixels in size.
		</td>
	</tr>
	<tr>
		<td>
			<b>extra_image</b>
		</td>
		<td>
			<b>optional</b> URL of a photo of your product. Link directly to the image, not the page where it is located. Same rules apply as main_image. You can specify one or more additional images separated by the character '|'. The total number of extra images plus the number of variation images must not exceed 20.
		</td>
	</tr>
	<tr>
		<td>
			<b>max_quanity</b>
		</td>
		<td>
			<b>optional</b> The maximum quantityof products per order.
		</td>
	</tr>
</table>

<b>Returns</b></br>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## Delete a Product
> Example</br>
Lets say you want to delete a product with id '10101'

> Example Request

```curl
> curl -X DELETE 'https://merchant.hopscotch.in/api/product/10101'
```

> Example Response

```json
{
    'code': 0,
    'data': {},
    'message': ''
}
```

Deletes the specified product. </br>

<b>HTTP Request Type: DELETE</b>

<b>Definition</b> </br>
DELETE https://merchant.hopscotch.in/api/product/{product_id}

<b>Returns</b></br>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## Enable a Product
> Example</br>
Assume your access token is "an_example_access_token" . If you had a product with id 101010 and you wanted to enable it, your parameters would be: </br></br>
product_id = 101010</br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/product/enable -d "product_id=101010&access_token=an_example_access_token"
```

> Example Response

```json
{
    'code': 0,
    'data': {},
    'message': ''
}
```

This API enables a product for sale.</br>
<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/product/enable 

<b>Parameters</b>
<table>
<tbody>
<tr>
<td><b>product_id</b></td>
<td></td>
</tr>
</tbody>
</table>

<b>Returns</b></br>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## Disable a Product
> Example</br>
Assume your access token is "an_example_access_token" . If you had a product with id 101010 and you wanted to disable it, your parameters would be: </br></br>
product_id = 101010</br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/product/disable -d "product_id=101010&access_token=an_example_access_token"
```

> Example Response

```json
{
    'code': 0,
    'data': {},
    'message': ''
}
```

This API disables a product for sale.</br>
<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/product/disable 

<b>Parameters</b>
<table>
<tbody>
<tr>
<td><b>product_id</b></td>
<td></td>
</tr>
</tbody>
</table>

<b>Returns</b></br>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## Retrieve a Product
> Example</br>
Assume your access token is "an_example_access_token". If you want to retrieve a product with the id 101010: </br></br>
product_id = 101010 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl "https://merchant.hopscotch.in/api/product?product_id=101010&access_token=an_example_access_token"
```

> Example Response

```json
{
	'code': 0,
	'data': {
		'product': 
			  {
			    'description': 'Example description',
			    'id': '101010',
			    'name': 'Cute Ring',
			    'number_sold': '0',
			    'review_status': 'approved',
			    'variants': [
			        {
			          'enabled': 'True',
			          'product_id': '101010',
			          'inventory': '11',
			          'msrp': '113.9',
			          'price': '110.9',
			          'shipping': '10.5',
			          'sku': 'AA1'
			      },
			      {
			          'enabled': 'True',
			          'product_id': '101010',
			          'inventory': '100',
			          'msrp': '19.9',
			          'price': '15.9',
			          'shipping': '10.5',
			          'sku': 'ZZ1'
			      }
			    ]
			  }
		},
	'message': ''
}	
```

Retrieve the details about a product which exists on the Hopscotch platform. You must have the unique product Id that was returned upon product creation. </br></br>

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/product

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>product_id</b>
		</td>
		<td>
			Must provide id. The unique Hopscotch identifier for this product
		</td>
	</tr>
</table>

<b>Returns</b></br>
Returns a product entity if a valid identifier was provided.

## List all Products
> Example</br>
Assume your access token is "an_example_access_token". If you would like to view your products updated after 2014-10-15 and before 2015-06-10 01:00:00 in groups of 2 and you would like to see the 10th group your parameters would be: </br></br>
start = 20 </br>
limit = 2 </br>
since = 2014-10-15 </br>
upto = 2015-06-10T01:00:00 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl "https://merchant.hopscotch.in/api/product/multi-get?limit=2&start=20&since=2014-10-15&access_token=an_example_access_token"
```

> Example Response

```json
{
	'code': 0,
	'data': {
			'products': [
			  {
			    'description': 'Example description',
			    'id': '101010',
			    'name': 'Cute Ring',
			    'number_sold': '0',
			    'review_status': 'approved',
			    'variants': [
			        {
			          'enabled': 'True',
			          'product_id': '101010',
			          'inventory': '11',
			          'msrp': '113.9',
			          'price': '110.9',
			          'shipping': '10.5',
			          'sku': 'AA1'
			      },
			      {
			          'enabled': 'True',
			          'product_id': '101010',
			          'inventory': '100',
			          'msrp': '19.9',
			          'price': '15.9',
			          'shipping': '10.5',
			          'sku': 'ZZ1'
			      }
			    ]
			  }, {
			    'description': 'Example Description',
			    'id': '101011',
			    'name': 'Fairisle Scarf',
			    'number_saves': '0',
			    'number_sold': '0',
			    'parent_sku': 'Fairisle Scarf',
			    'review_status': 'rejected',
			    'variants': [{
			          'enabled': 'True',
			          'product_id': '101011',
			          'inventory': '1010',
			          'msrp': '25.9',
			          'price': '21.91',
			          'shipping': '10.0',
			          'sku': 'AA4'
			      },
			      {
			          'enabled': 'True',
			          'product_id': '101011',
			          'inventory': '1100',
			          'msrp': '21.99',
			          'price': '21.91',
			          'shipping': '11.0',
			          'sku': 'AAB'
			      }
			    ]
			  }
			]
		},
	'message': '',
	'paging': 
		{
			'next': 'https://merchant.hopscotch.in/api/product/multi-get?start=22&limit=2&since=2014-10-15&access_token=an_example_access_token',
			'previous': 'https://merchant.hopscotch.in/api/product/multi-get?start=18&limit=2&since=2014-10-15&access_token=an_example_access_token'
		}
}	
```

Returns a list of all your products currently on the Hopscotch platform. If you have a high number of products the response will be paginated. The response will contain the URL for fetching the next page of products.</br>

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/product/multi-get

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
			<b>optional</b> A limit on the number of warehouses that can be returned. Limit can range from 1 to 250 items and the default is 50
		</td>
	</tr>
	<tr>
		<td>
			<b>since</b>
		</td>
		<td>
			<b>optional</b> A date/time string in the format YYYY-MM-DD or YYYY-MM-DDTHH:MM:SS. If a date or time is provided, only products updated since the given date or time will be fetched. Default is to fetch all.
		</td>
	</tr>
	<tr>
		<td>
			<b>upto</b>
		</td>
		<td>
			<b>optional</b> A date/time string in the format YYYY-MM-DD or YYYY-MM-DDTHH:MM:SS. If a date or time is provided, only products updated before the given date or time will be fetched. Default is to fetch all updated products until now.
		</td>
	</tr>
	<tr>
		<td>
			<b>show_rejected</b>
		</td>
		<td>
			<b>optional</b> If specified to 'true', this API will return all products including those inappropriate products that were rejected during review.
		</td>
	</tr>
</table>

<b>Returns</b></br>
Response will contain a list of product objects as well as a 'paging' field with paging options if needed.