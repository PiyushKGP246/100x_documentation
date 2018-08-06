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
</tbody>
</table>

## Create a Warehouse

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
</tbody>
</table>

<b>Returns</b>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## Update a Warehouse

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
</tbody>
</table>

<b>Returns</b>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.

## Delete a Warehouse

## Make Default Warehouse

<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
https://merchant.hopscotch.in/api/warehouse/default?

<b>Returns</b>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.