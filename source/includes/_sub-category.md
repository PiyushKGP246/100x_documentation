# Sub Category
With this API you can get list of Hopscotch sub-categories.

<b>Attributes</b>
<table>
	<tr>
		<td>
			<b>sub_category_id</b>
		</td>
		<td>
		</td>
	</tr>
	<tr>
		<td>
			<b>sub_category_name</b>
		</td>
		<td>
			Unique identifier assigned by Hopscotch to sub-categories. 
		</td>
	</tr>
</table>

## List Sub-Categories
> Example</br>
Assume your access token is "an_example_access_token". If you would like to list all sub-categories associated with category id '1', your parameters would be: </br></br>
category_id = 1 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl "https://merchant.hopscotch.in/api/sub-category?category_id=1&access_token=an_example_access_token"
```

> Example Response

```json
{
	'code': 0,
	'data': {
			'sub_categories' : [
			{
				"sub_category_id": 1,
				"sub_category_name" : "Apparel - Children"
			}, {
				"sub_category_id": 2,
				"sub_category_name" : "Apparel - Women"
			}
		]
	},
	'message': ''
}	
```

Returns a list of all Hopscotch sub-categories.</br>

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/sub-category

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>category_id</b>
		</td>
		<td>
			Id for which sub-categories has to be fetched.
		</td>
	</tr>
</table>

<b>Returns</b></br>
Response will contain a list of sub-category objects.