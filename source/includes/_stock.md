# Product Stocks

## Update Stock
> Example</br>
Assume your access token is "an_example_access_token". If you would like to update the inventory of SKU "aaa" to 10 for warehouse id '1', and SKU "bbb" to 20, your parameter would be: </br></br>
skus = [{"sku": "aaa", "inventory": 10, "warehouse_id": 1}, {"sku": "bbb", "inventory": 20}] </br>
access_token = an_example_access_token

> Example Request

```curl
> curl "https://merchant.hopscotch.in/api/variant/bulk-inventory-update -d "access_token=an_example_access_token&format=json&skus=[{"sku": "aaa", "inventory": 10, "warehouse_id": 1}, {"sku": "bbb", "inventory": 20}]"
```

> Example Response

```json
{
  "message": "",
  "code": 0,
  "data": {
    "job_id": "59e15a939a64f71c5024a1e3"
  }
}
```

Bulk update inventory of up to 100,000 existing product variations. This API is non-blocking, a job_id will be returned. Use <a href="#bulk-inventory-update-job-status">Get Job Status of Variation Bulk Inventory Update </a>to get the current status of the job. Once the job is completed, use the following APIs to get the results: <a href="#bulk-inventory-successfully-updated-skus-job-status">Get Successfully Updated SKUs from Variation Bulk Inventory Update </a>, <a href = "#errors-from-bulk-inventory-update">Get Errors from Variation Bulk Inventory Update</a>. </br> </br>
<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/variant/update-inventory

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>skus</b>
		</td>
		<td>
			A json array of SKU objects. Each SKU object must have attribute sku as the unique identifier of a variation. Use the attribute inventory to update the inventory of a variation, and attribute warehouse to specify the inventory associated with. If the warehouse_id is not provided, the inventory will be applied to the DEFAULT warehouse.
		</td>
	</tr>
</table>

<b>Returns</b></br>
A job_id will be returned if request is successful.

<h2 id="bulk-inventory-update-job-status"> Get Job Status of Variation Bulk Inventory Update </h2>
> Example </br>
Assume your access token is "an_example_access_token". Suppose you want to check the status of your bulk inventory update for product variations with job_id "59e00339b2d5b8367ac3e8bd": </br> </br>
job_id = 59e00339b2d5b8367ac3e8bd </br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/variant/get-bulk-inventory-update-job-status -d "job_id='59e00339b2d5b8367ac3e8bd'&access_token=an_example_access_token"
```

> Example Response

```json
{
  "message": "",
  "code": 0,
  "data": {
    "status": 4,
    "state": "FINISHED",
    "merchant_id": "515a29092f533b2778a7f625",
    "success_count": 10
    "end_time": 2017-10-17T05:48:21,
    "failure_count": 10,
    "start_time": "2017-10-17T05:46:51",
    "processed_count": 20,
    "results": {
        "successes": "https://merchant.hopscotch.in/api/variant/get-bulk-inventory-update-job-successes?job_id=59e00339b2d5b8367ac3e8bd"
        "failures": "https://merchant.hopscotch.in/variant/get-bulk-inventory-update-job-failures?job_id=59e00339b2d5b8367ac3e8bd"
    }
    "id": "59e5994b9a64f72cafea7730",
    "uploader_id": "5ae5923b9a64f72cab4a772a"
  }
}
```

Call this to get the current state and progress for your Product Variations bulk inventory update.

<b>HTTP Request Type: GET</b>

<b>Definition</b> </br>
GET https://merchant.hopscotch.in/api/variant/get-bulk-inventory-update-job-status

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>job_id</b>
		</td>
		<td>
			The unique identifier you received from bulk inventory update production variations (/variant/update-inventory)
		</td>
	</tr>
	<tr>
		<td>
			<b>Returns</b>
		</td>
		<td>
			The status of the specified bulk inventory update job and current number of processed items, as well as the number of successes and failures.
		</td>
	</tr>
</table>

<h2 id="bulk-inventory-successfully-updated-skus-job-status"> Get Successfully Updated SKUs from Variation Bulk Inventory Update </h2>
> Example </br>
Assume your access token is "an_example_access_token". Suppose you want to check the first 5 SKUs from your bulk inventory update for product variations with job_id "59e00339b2d5b8367ac3e8bd" that were updated successfully: </br> </br>
job_id = 59e00339b2d5b8367ac3e8bd </br>
access_token = an_example_access_token </br>
limit = 5

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/variant/get-bulk-inventory-update-job-successes -d "job_id='59e00339b2d5b8367ac3e8bd'&access_token=an_example_access_token&limit='5'"
```

> Example Response

```json
{
  "message": "",
  "code": 0,
  "data": {
    "successes": [
      "SKU1",
      "SKU2",
      "SKU3",
      "SKU4",
      "SKU5"
    ]
  },
  "paging": {
    "next": "https://merchant.hopscotch.in/api/variant/get-bulk-inventory-update-job-successes?start=3&limit=3"
  }
}	
```

Call this to get a list of all SKUs that were successfully updated from your Product Variations bulk inventory update.

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/variant/get-bulk-inventory-update-job-successes

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>job_id</b>
		</td>
		<td>
			The unique identifier you received from bulk update production variations (/variant/update-inventory)
		</td>
	</tr>
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
			<b>optional</b> A limit on the number of items that can be returned. Limit can range from 1 to 250 items and the default is 50
		</td>
	</tr>
	<tr>
		<td>
			<b>Returns</b>
		</td>
		<td>
			A list of successfully updated SKUs. If the response requires pagination the 'paging' field will contain the URL for the next page of results.
		</td>
	</tr>
</table>

<h2 id="errors-from-bulk-inventory-update"> Get Errors from Variation Bulk Inventory Update </h2>
> Example </br>
Assume your access token is "an_example_access_token". Suppose you want to check the first 3 errors that were raised from your bulk inventory update for product variations with job_id "59e00339b2d5b8367ac3e8bd": </br> </br>
job_id = 59e00339b2d5b8367ac3e8bd </br>
access_token = an_example_access_token </br>
limit = 3

> Example Request

```curl
> curl https://merchant.hopscotch.in/variant/get-bulk-inventory-update-job-failures -d "job_id='59e00339b2d5b8367ac3e8bd'&access_token=an_example_access_token&limit='3'"
```

> Example Response

```json
{
  "message": "",
  "code": 0,
  "data": {
    "errors": [
      {
        "sku": "fake_sku1",
        "error_code": 29,
        "error": "Your store does not have product with SKU 'fake_sku1', therefore no update can be done."
      },
      {
        "sku": "fake_sku2",
        "error_code": 29,
        "error": "Your store does not have product with SKU 'fake_sku2', therefore no update can be done."
      },
      {
        "sku": "fake_sku3",
        "error_code": 29,
        "error": "Your store does not have product with SKU 'fake_sku3', therefore no update can be done."
      }
    ]
  },
  "paging": {
    "next": "https://merchant.hopscotch.in/variant/get-bulk-inventory-update-job-failures?start=3&limit=3"
  }
}	
```

Call this to get a list of all errors encountered from your Product Variations bulk inventory update.

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/variant/get-bulk-inventory-update-job-failures

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>job_id</b>
		</td>
		<td>
			The unique identifier you received from bulk update production variations (/variant/update-inventory)
		</td>
	</tr>
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
			<b>optional</b> A limit on the number of items that can be returned. Limit can range from 1 to 250 items and the default is 50
		</td>
	</tr>
	<tr>
		<td>
			<b>Returns</b>
		</td>
		<td>
			A list of errors. If the response requires pagination the 'paging' field will contain the URL for the next page of results.	
		</td>
	</tr>
</table>

## List stock
- brand
- product
- sku
- warehouse