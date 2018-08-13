# Product Variation

The product variation entity represents a SKU that is for sale. It has a price, shipping price and a size. Each product variation belongs to one product and each product has at least one product variation. A user always buys a product variation, and each SKU in your system will map to one product variation in Hopscotch.

With this API you can create and update product variations. You can also retrieve details about specific product variations or page through all your product variations.

<b>Attributes</b>

## Create a Product Variation
> Example</br>
Assume your access token is "an_example_access_token" . If you have a product with a parent sku red-shoe and you would like to add a variant for the size 12, with sku red-shoe-12, your parameters would be:</br></br>
parent_sku = red-shoe </br>
sku = red-shoe-12 </br>
inventory = 10 </br>
price = 10 </br>
shipping = 3 </br>
size = 12 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/variant/add -d "parent_sku=red-shoe&sku=red-shoe-12&inventory=10&price=10&shipping=3&size=12&access_token=an_example_access_token"
```

> Example Response

```json
{
    'message' : '',
    'code' : 0,
    'data' : 
    	{ 
    		"variant_id" : 101010
        }
}
```

To add a new variation to a product you can create a product variation. For example, a product has sizes Large and Extra-Large and you wanted to add size Medium, you would create a new product variation with this API. If you add a new variation with the existing size pair, it will update the exisiting variation instead of creating a new variation. </br>

<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/variant/add

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
			<b>sku</b>
		</td>
		<td>
			The unique identifier that your system uses to recognize this variation
		</td>
	</tr>
	<tr>
		<td>
			<b>color</b>
		</td>
		<td>
			<b>optional</b> The color of the variation. Example: red, blue, green. Note: color and size cannot both be empty. The color and size pair should not be repetitive size.
		</td>
	</tr>
	<tr>
		<td>
			<b>size</b>
		</td>
		<td>
			<b>optional</b> The size of the variation. Example: Large, Medium, Small, 5, 6, 7.5 Note: color and size cannot both be empty. The color and size pair should not be repetitive.
		</td>
	</tr>
	<tr>
		<td>
			<b>inventory</b>
		</td>
		<td>
			The physical quantities you have for this variation, max 500,000
		</td>
	</tr>
	<tr>
		<td>
			<b>warehouse_name</b>
		</td>
		<td>
		</td>
	</tr>
	<tr>
		<td>
			<b>price</b>
		</td>
		<td>
			The price of the variation when the user purchases one, max 100,000
		</td>
	</tr>
	<tr>
		<td>
			<b>shipping</b>
		</td>
		<td>
			The shipping of the product when the user purchases one, max 1000
		</td>
	</tr>
	<tr>
		<td>
			<b>msrp</b>
		</td>
		<td>
			<b>optional</b> Manufacturer's Suggested Retail Price. This field is recommended as it will show as a strikethrough price on Hopscotch and appears above the selling price for the product.
		</td>
	</tr>
	<tr>
		<td>
			<b>shipping_time</b>
		</td>
		<td>
			<b>optional</b> The amount of time it takes for the shipment to reach the buyer. Please also factor in the time it will take to fulfill and ship the item. Provide a time range in number of days. Lower bound cannot be less than 2 days. Upper bound must be at least 5 days after the lower bound. Example: 15-20    
		</td>
	</tr>
	<tr>
		<td>
			<b>main_image</b>
		</td>
		<td>
			<b>optional</b> URL of a photo for this product variation. Provide this when you have different pictures for different product variation of the product. If left out, it'll use the main_image of the product with the provided parent_sku. Link directly to the image, not the page where it is located. We accept JPEG, PNG or GIF format. Images should be at least 100 x 100 pixels in size.
		</td>
	</tr>
	<tr>
		<td>
			<b>length</b>
		</td>
		<td>
			<b>optional</b> The length of your product that will be packaged to ship to customer (Units in cm) </br>
			Acceptable: 10
		</td>
	</tr>
	<tr>
		<td>
			<b>width</b>
		</td>
		<td>
			<b>optional</b> The width of your product that will be packaged to ship to customer (Units in cm) </br>
			Acceptable: 13.40
		</td>
	</tr>
	<tr>
		<td>
			<b>height</b>
		</td>
		<td>
			<b>optional</b> The height of your product that will be packaged to ship to customer (Units in cm) </br>
			Acceptable: 13.40
		</td>
	</tr>
	<tr>
		<td>
			<b>weight</b>
		</td>
		<td>
			<b>optional</b> The weight of your product that will be packaged to ship to customer (Units in g) </br>
			Acceptable: 151.5 </br>
			Acceptable: 10 </br>
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
			<b>declared_value</b>
		</td>
		<td>
			<b>optional</b> The price of your product that will be declared to custom. </br>
			Acceptable: $100.99 </br>
			Acceptable: 10.99 </br>
			Unacceptable: $49.99 + S/H
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
			<b><has_liquid/b>
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
</table>

<b>Return</b> </br>
If the request was successful and a Variant was added to the supplied Product, then the response will contain Hopscotch identifier, variant_id.

## Update a Product Variation
> Example</br>
Assume your access token is "an_example_access_token" . If you have an item with the SKU 'blue-shoe-11' and it has the wrong size and you need to update its price, shipping and inventory your parameters would be:</br></br>
sku = blue-shoe-11 </br>
price = 10.11 </br>
shipping = 10.00 </br>
inventory = 1000 </br>
access_token = an_example_access_token </br>
Lets say you didn't need to update price, then you would omit this parameter from your request.

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/variant/update -d "sku=blue-shoe-11&price=10.11&shipping=10.00&inventory=1000&access_token=an_example_access_token"
```

> Example Response

```json
{
    'message' : '',
    'code' : 0,
    'data': {}
}
```

Updates the specified variation by updating the attributes of the parameters passed in the request. Any attribute not provided will be left unchanged. </br>

This request can only update attributes specific to variations and cannot be used to update any attribute of a Product.</br>

<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/variant/update

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

<b>Return</b> </br>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## Delete a Product Variation
> Example</br>
Lets say you want to delete a sku 'blue-shoe-11'

> Example Request

```curl
> curl -X DELETE 'https://merchant.hopscotch.in/api/variant/blue-shoe-11'
```

> Example Response

```json
{
    'code': 0,
    'data': {},
    'message': ''
}
```

Deletes the specified sku. </br>

<b>HTTP Request Type: DELETE</b>

<b>Definition</b> </br>
DELETE https://merchant.hopscotch.in/api/variant/{sku}

<b>Returns</b></br>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## Enable a Product Variation
> Example</br>
Assume your access token is "an_example_access_token" . If you have an item with the SKU 'blue-shoe-11' and you want to enable it, your parameters would be:</br></br>
sku = blue-shoe-11 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/variant/enable -d "sku=blue-shoe-11&access_token=an_example_access_token"
```

> Example Response

```json
{
    'code': 0,
    'data': {},
    'message': ''
}
```

Enable a product variation. This marks the product variation available for sale.</br>
<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/variant/enable 

<b>Parameters</b>
<table>
<tbody>
<tr>
<td><b>sku</b></td>
<td>The unique identifier for the item you would like to update</td>
</tr>
</tbody>
</table>

<b>Returns</b></br>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## Disable a Product Variation
> Example</br>
Assume your access token is "an_example_access_token" . If you have an item with the SKU 'blue-shoe-11' and you want to disable it, your parameters would be:</br></br>
sku = blue-shoe-11 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/variant/disable -d "sku=blue-shoe-11&access_token=an_example_access_token"
```

> Example Response

```json
{
    'code': 0,
    'data': {},
    'message': ''
}
```

Disable a product variation. This marks the product variation unavailable for sale.</br>
<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/variant/disable 

<b>Parameters</b>
<table>
<tbody>
<tr>
<td><b>sku</b></td>
<td>The unique identifier for the item you would like to update</td>
</tr>
</tbody>
</table>

<b>Returns</b></br>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## Retrieve a Product Variation
> Example</br>
Assume your access token is "an_example_access_token" . If your store has an item with sku "red-shoe-8" and you would like to know its state on with your request's parameters would be: </br>
sku = red-shoe-8 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl "https://merchant.hopscotch.in/api/variant?sku=red-shoe-8&access_token=an_example_access_token"
```

> Example Response

```json
{'code': 0,
 'data': {
 	'Variant': 
	 	{
	 		'enabled': 'True',
			'product_id' : '10101',
			'inventory': '1000',
			'msrp': '21100.0',
			'price': '100.0',
			'shipping': '10.0',
			'sku': 'red-shoe-8'
		}
	},
 'message': ''
}
```

Retrieves the details of an existing product variation. Provide the SKU of the product variation and Wish will return details about the corresponding product variation. </br></br>

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/variant

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>sku</b>
		</td>
		<td>
			The unique identifier of the item in your system.
		</td>
	</tr>
	<tr>
		<td>
			<b>warehouse_name</b>
		</td>
		<td>
			<b>optional</b> The warehouse from where the variant shipping and inventory are fetched. If not specified, default warehouse shipping and inventory are used.
		</td>
	</tr>
</table>

<b>Returns</b></br>
For successful requests the response will contain a Variant object in the requested format.

## List all Product Variations
> Example</br>
Assume your access token is "an_example_access_token" . If you would like to fetch information about all your items in groups of 2 and you would like to see the 10th group </br></br>
start = 20 </br>
limit = 2 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl "https://merchant.hopscotch.in/api/variant/multi-get?limit=2&start=20&access_token=an_example_access_token"
```

> Example Response

```json
{
	'code': 0,
	 'data': [
	    {
	      'Variant': 
	        {
	          'enabled': 'True',
	          'product_id' : '10101',
	          'inventory': '1314',
	          'msrp': '150.0',
	          'price': '100.0',
	          'shipping': '21.0',
	          'sku': 'MMM'
	          },
	    }
	    {
	      'Variant': 
	        {
	          'enabled': 'True',
	          'product_id' : '10101',
	          'inventory': '917',
	          'msrp': '100.0',
	          'price': '50.0',
	          'shipping': '9.81',
	          'sku': 'DD1111'
	        }
	    }
	  ],
	 'message': '',
	 'paging': {
	    'next': 'https://merchant.wish.com/api/v2/variant/multi-get?start=22&limit=2&access_token=an_example_access_token',
	    'previous': 'https://merchant.wish.com/api/v2/variant/multi-get?start=18&limit=2&access_token=an_example_access_token'
	  }
}
```

Returns a list of all your product variations currently on the Hopscotch platform. This API is useful to paginate through all the SKUs that you have uploaded to Hopscotch. If the number of results is too large the full result set may require pagination.</br>

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/variant/multi-get

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
			<b>warehouse_name</b>
		</td>
		<td>
			<b>optional</b> The warehouse from where the variants' shippings and inventories are fetched. If not specified, default warehouse variation shippings and inventories are used.
		</td>
	</tr>
</table>

<b>Returns</b></br>
For successful requests the response data will contain a list of product variation objects. If the response requires pagination the 'paging' field will contain the URL for the next page of results.