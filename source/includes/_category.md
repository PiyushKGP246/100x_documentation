# Category
With this API you can get list of Hopscotch categories.

<b>Attributes</b>
<table>
	<tr>
		<td>
			<b>category_id</b>
		</td>
		<td>
			Unique identifier assigned by Hopscotch to categories. 
		</td>
	</tr>
	<tr>
		<td>
			<b>category_name</b>
		</td>
		<td>
			The name which Hopscotch has given the category. 
		</td>
	</tr>
</table>

## List Categories
> Example Request

```curl
> curl "https://merchant.hopscotch.in/api/category?access_token=an_example_access_token"
```

> Example Response

```json
{
	'code': 0,
	'data': {
			'categories' : [
			{
				"category_id": 1,
				"category_name" : "Apparel"
			}, {
				"category_id": 2,
				"category_name" : "Footwear"
			}
		]
	},
	'message': ''
}	
```

Returns a list of all Hopscotch categories.</br>

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/category

<b>Returns</b></br>
Response will contain a list of category objects.