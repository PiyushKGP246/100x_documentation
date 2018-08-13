# Warehouse

The Warehouse object represents separate Warehouses and shipping options you provide. With this API, you can create, update, delete and make default warehouse.

<b>Attributes</b>
<table>
<tbody>
<tr>
<td><b>wms_code</b></td>
<td></td>
</tr>
<tr>
<td><b>description</b></td>
<td></td>
</tr>
<tr>
<td><b>name</b></td>
<td></td>
</tr>
<tr>
<td><b>wms_prefix</b></td>
<td></td>
</tr>
<tr>
<td><b>status</b></td>
<td></td>
</tr>
<tr>
<td><b>wms_address</b></td>
<td></td>
</tr>
<tr>
<td><b>location</b></td>
<td></td>
</tr>
<tr>
<td><b>sor_return_address</b></td>
<td></td>
</tr>
<tr>
<td><b>is_po_receiving</b></td>
<td></td>
</tr>
<tr>
<td><b>is_default</b></td>
<td></td>
</tr>
</tbody>
</table>

## Create a Warehouse
> Example</br>
Assume your access token is "an_example_access_token". If you have a warehouse with name "China Warehouse" with code 'CHNW', address as '...China' in location 'China'. If it is active and default and you want the description to be 'China Warehouse' and warehouse prefix as 'CHN', your parameters would be: </br></br>
description = China Warehouse </br>
name = China Warehouse </br>
wms_prefix = CHN </br>
wms_code = CHNW </br>
status = 1 </br>
wms_address = ...China </br>
location = China </br>
sor_return_address = ...China </br>
is_po_receiving = 1 </br>
is_default = 1

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/warehouse/add -d "description=China Warehouse&name=China Warehouse&wms_prefix=CHN&wms_code=CHNW&status=1&wms_address=...China&location=China&sor_return_address=...China&is_po_receiving=1&is_default=1&access_token=an_example_access_token"
```

> Example Response

```json
{
    'message' : '',
    'code' : 0,
    'data' : 
    	{ 
    		"warehouse_id" : 101010
        }
}
```

Use below endpoint to create a new warehouse. </br>
<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/warehouse/add

<b>Parameters</b>
<table>
<tbody>
<tr>
<td><b>wms_code</b></td>
<td></td>
</tr>
<tr>
<td><b>description</b></td>
<td></td>
</tr>
<tr>
<td><b>name</b></td>
<td></td>
</tr>
<tr>
<td><b>wms_prefix</b></td>
<td></td>
</tr>
<tr>
<td><b>status</b></td>
<td></td>
</tr>
<tr>
<td><b>wms_address</b></td>
<td></td>
</tr>
<tr>
<td><b>location</b></td>
<td></td>
</tr>
<tr>
<td><b>sor_return_address</b></td>
<td></td>
</tr>
<tr>
<td><b>is_po_receiving</b></td>
<td></td>
</tr>
<tr>
<td><b>is_default</b></td>
<td></td>
</tr>
</tbody>
</table>

<b>Returns</b></br>
Upon success, a warehouse will be created and warehouse_id will be returned in the response.

## Update a Warehouse
> Example</br>
Assume your access token is "an_example_access_token" . If you had a warehouse with id 101010 and you wanted to change the wms_code to "CH", update the description to "China-Apparel Warehouse" your parameters would be: </br></br>
id = 101010 </br>
wms_code = CH </br>
description = China-Apparel Warehouse </br>
access_token = an_example_access_token </br>
If you did not want to update the description, you would omit that parameter from your API call.

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/warehouse/update -d "id=101010&wms_code=CH&description=China-Apparel Warehouse&access_token=an_example_access_token"
```

> Example Response

```json
{
    'code': 0,
    'data': {},
    'message': ''
}
```

Updates the specified warehouse with the parameters passed in the request. Any attribute not provided will be left unchanged. For example, if you pass the name parameter we will update the name of the warehouse and leave everything else unchanged.</br>
<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/warehouse/update

<b>Parameters</b>
<table>
<tbody>
<tr>
<td><b>wms_code</b></td>
<td></td>
</tr>
<tr>
<td><b>description</b></td>
<td></td>
</tr>
<tr>
<td><b>name</b></td>
<td></td>
</tr>
<tr>
<td><b>wms_prefix</b></td>
<td></td>
</tr>
<tr>
<td><b>status</b></td>
<td></td>
</tr>
<tr>
<td><b>wms_address</b></td>
<td></td>
</tr>
<tr>
<td><b>location</b></td>
<td></td>
</tr>
<tr>
<td><b>sor_return_address</b></td>
<td></td>
</tr>
<tr>
<td><b>is_po_receiving</b></td>
<td></td>
</tr>
<tr>
<td><b>is_default</b></td>
<td></td>
</tr>
</tbody>
</table>

<b>Returns</b></br>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## Delete a Warehouse
> Example</br>
Lets say you want to delete warehouse with warehouse_id '1'

> Example Request

```curl
> curl -X DELETE 'https://merchant.hopscotch.in/api/warehouse/{warehouse_id}'
```

> Example Response

```json
{
    'code': 0,
    'data': {},
    'message': ''
}
```

Deletes the specified warehouse. </br>
<b>HTTP Request Type: DELETE</b>

<b>Definition</b> </br>
DELETE https://merchant.hopscotch.in/api/warehouse/{warehouse_id}

<b>Returns</b></br>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## Make Default Warehouse
> Example</br>
Assume your access token is "an_example_access_token" . If you have a warehouse with id 101010 and you wanted to make it as default, your parameters would be: </br></br>
warehouse_id = 101010 </br>
access_token = an_example_access_token </br>

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/warehouse/default -d "warehouse_id=101010&access_token=an_example_access_token"
```

> Example Response

```json
{
    'code': 0,
    'data': {},
    'message': ''
}
```

Makes a warehouse default for shipping and sku inventory upload.</br>
<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/warehouse/default

<b>Parameters</b>
<table>
<tbody>
<tr>
<td><b>warehouse_id</b></td>
<td></td>
</tr>
</tbody>
</table>

<b>Returns</b></br>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## List Warehouse
> Example</br>
Assume your access token is "an_example_access_token" . If you would like to view your warehoused in groups of 2 and you would like to see the 10th group your parameters would be: </br></br>
start = 20 </br>
limit = 2 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl "https://merchant.hopscotch.in/api/warehouse/multi-get?limit=2&start=20&access_token=an_example_access_token"
```

> Example Response

```json
{
	'code': 0,
	'data': {
			'warehouses' : [
			{
				'wms_code': 'CHNW',	
				'description': 'China Warehouse',	
				'name': 'China Warehouse',	
				'wms_prefix': 'CHN',	
				'status': '1',	
				'wms_address': '...China',	
				'location': 'China',	
				'sor_return_address': '...China',	
				'is_po_receiving': '1',
				'is_default': '0'	
			}, {
				'wms_code': 'XN',	
				'description': 'Xian Warehouse',	
				'name': 'Xian Warehouse',	
				'wms_prefix': 'XN',	
				'status': '1',	
				'wms_address': '...China',	
				'location': 'China',	
				'sor_return_address': '...China',	
				'is_po_receiving': '1',
				'is_default': '1'	
			}
		]
	},
	'message': '',
	'paging': 
		{
			'next': 'https://merchant.hopscotch.in/api/warehouse/multi-get?start=22&limit=2&access_token=an_example_access_token',
			'previous': 'https://merchant.hopscotch.in/api/warehouse/multi-get?start=18&limit=2&access_token=an_example_access_token'
		}
}	
```

Returns a list of all your warehouses currently integrated with the Hopscotch platform. If you have a high number of warehouses the response will be paginated. The response will contain the URL for fetching the next page of warehouses.</br>

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/warehouse/multi-get

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
</table>

<b>Returns</b></br>
Response will contain a list of warehouse objects as well as a 'paging' field with paging options if needed.