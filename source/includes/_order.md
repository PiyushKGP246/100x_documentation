# Order
For every item that Hopscotch from your store there is a corresponding Order. Each order corresponds with one SKU. The order object provides you with the destination, item and any other required information to fulfill a user's order.

With this API you can fetch order that require fulfillment and orders that have been updated since a given period. This API also allows you to fulfill one order at a time by providing tracking information for an order.

<b>Order State</b> </br>
Orders can be in several different states depending on what has happened. State 'APPROVED' means that the order is ready to ship. State 'SHIPPED' means that the order has been marked as shipped by you. State 'REFUNDED' means that the order has been refunded to the user and should not be fulfilled. State 'REQUIRE_REVIEW' means that the order is under review for fraudulent activity and should not be fulfilled.

<b>Attributes</b>


## Retrieve an Order
> Example</br>
Assume your access token is "an_example_access_token" . If you have an order with order_id "123456789009876543210164" and you would like to retrieve any updates to it:</br></br>
id = 123456789009876543210164 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/order?id=123456789009876543210164&access_token=an_example_access_token
```

> Example Response

```json
{
    "message": "",
    "code": 0,
    "data": {
        "Order": {
            "last_updated": "2018-04-24T07:30:52",
            "order_time": "2018-04-23T05:24:53",
            "color": "lightbrown",
            "price": "1.0",
            "ShippingDetail": {
                "phone_number": "+86 13816792755",
                "city": "Shanghai",
                "state": "Shanghai",
                "name": "EPC Shanghai - 542195",
                "country": "CN",
                "zipcode": "201901",
                "street_address1": "No.419 Gongyue RD Baoshan District Shanghai - 542195"
            },
            "shipped_date": "2018-04-24",
            "cost": "0.85",
            "shipping_cost": "0.85",
            "requires_delivery_confirmation": "False",
            "product_image_url": "https://contestimg.hopscotch.com/api/webimage/5abfd8801ab08a1da66447ad-normal.jpg?cache_buster=4b66fc88f4ad4c7c3176cd07fbfab237",
            "size": "One Size",
            "sku": "aa2620a43d9844313509e019-light brown-One Size",
            "shipping_provider": "Ekart",
            "order_total": "1.7",
            "product_id": "10101",
            "tracking_confirmed": "True",
            "state": "SHIPPED",
            "shipping": "1.0",
            "OriginalShippingDetail": {
                "phone_number": "01233434",
                "city": "Edinburg",
                "state": "Texas",
                "name": "Mabel hinojosa",
                "country": "US",
                "zipcode": "78511",
                "street_address1": "aaaa n terry rd"
            },
            "order_id": "aadd6e252ad6c17fd4542195",
            "tracking_number": "WI0000000aa056EPC",
            "released_to_merchant_time": "2018-04-23T13:30:50",
            "is_combined_order": "True",
            "tracking_confirmed_date": "2018-04-24T15:43:40",
            "quantity": "100",
            "product_name": "Waterproof Eyebrow Pencil Pen Eye Brow Liner Cosmetic Makeup Beauty Tool Lasting waterproof eye brow pencil",
            "transaction_id": "aadd6e22a016522e7b6f781e",
            "buyer_id": "aa1900f61983801052dec409",
            "fine_ids": ["5ab4e367ae3004ebb12c28ab"]
        }
    }
}
```

Retrieves the details of an existing order. Supply the unique identifier for the order and if one exists this API will return the corresponding order. Each order will have all the information you need to fulfill it

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/order

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>id</b>
		</td>
		<td>
			Hopscotch's unique identifier for the order (order_id in the Order object)
		</td>
	</tr>
</table>

## Retrieve Recently Changed Orders
> Example</br>
Assume your access token is "an_example_access_token" . If you use this API to sync Hopscotch orders into your order tracking software and you need all the orders that have changed since Jan 20, 2014 and you would like them in pages of 100 and you need the second page: (And you would like to get the original shipping details) </br></br>
start = 200 </br>
limit = 100 </br>
since = 2014-01-20 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/order/multi-get?start=200&limit=100&since=2014-01-20&access_token=an_example_access_token
```

> Example Response

```json
{
    "message": "",
    "code": 0,
    "data": [
        {
            "Order": {
                "last_updated": "2018-04-20T09:58:20",
                "order_time": "2018-04-15T22:06:32",
                "color": "white",
                "price": "8.0",
                "ShippingDetail": {
                    "phone_number": "3282833435",
                    "city": "Phillsburfg%b",
                    "state": "New Jersey",
                    "name": "John",
                    "country": "US",
                    "zipcode": "08865",
                    "street_address1": "111 Thomas St"
                },
                "shipped_date": "2018-04-20",
                "cost": "6.8",
                "shipping_cost": "5.1",
                "requires_delivery_confirmation": "True",
                "product_image_url": "https://contestimg.hopscotch.com/api/webimage/5a4a42ffd20e930b10742434-normal.jpg?cache_buster=60a9f08ac10fba8a58d571996f336a3f",
                "size": "7(EUR37)",
                "sku": "aaf3106_7_White",
                "shipping_provider": "EMS",
                "order_total": "11.9",
                "product_id": "101012",
                "tracking_confirmed": "True",
                "state": "SHIPPED",
                "shipping": "6.0",
                "order_id": "aad3cce86cb7a067f1680a92",
                "tracking_number": "LY113628433CN",
                "released_to_merchant_time": "2018-04-16T06:20:21",
                "is_combined_order": "False",
                "tracking_confirmed_date": "2018-04-24T12:15:48",
                "quantity": "1",
                "product_name": "Fashion Womens Sneakers Breathable Mesh Running Sports Shoes",
                "transaction_id": "aad3cce5d130801451d77758",
                "buyer_id": "aad2fd90c6b752f87cdd4f95",
                "fine_ids": ["5ab4e367ae3004ebb12c28ab"]
            }
        },
        {
            "Order": {
                "last_updated": "2018-04-20T07:09:09",
                "order_time": "2018-03-12T20:23:25",
                "color": "rose",
                "price": "8.0",
                "ShippingDetail": {
                    "phone_number": "+86 13816792755",
                    "city": "Shanghai",
                    "state": "Shanghai",
                    "name": "EPC Shanghai - 088220",
                    "country": "CN",
                    "zipcode": "201901",
                    "street_address1": "No.419 Gongyue RD Baoshan District Shanghai - 088220"
                },
                "shipped_date": "2018-03-15",
                "cost": "6.8",
                "shipping_cost": "5.1",
                "requires_delivery_confirmation": "True",
                "product_image_url": "https://contestimg.hopscotch.com/api/webimage/5a4a42ffd20e930b10742434-normal.jpg?cache_buster=60a9f08ac10fba8a58d571996f336a3f",
                "size": "6(EUR35)",
                "sku": "aaf31048_6_Rose",
                "shipping_provider": "Ekart",
                "order_total": "11.9",
                "product_id": "10101",
                "tracking_confirmed": "True",
                "state": "SHIPPED",
                "shipping": "6.0",
                "OriginalShippingDetail": {
                    "phone_number": "206446113765",
                    "city": "Des moines",
                    "state": "Washington",
                    "name": "Uyen John",
                    "country": "US",
                    "zipcode": "98198",
                    "street_address1": "1111 marine view dr. S"
                },
                "order_id": "aaa6e1bd631b6c703c088220",
                "tracking_number": "WI110000001743EPC",
                "released_to_merchant_time": "2018-03-13T04:31:02",
                "is_combined_order": "True",
                "tracking_confirmed_date": "2018-03-15T15:54:24",
                "quantity": "1",
                "product_name": "Fashion Womens Sneakers Breathable Mesh Running Sports Shoes",
                "transaction_id": "aaa6e1bcb40365735be165a9",
                "buyer_id": "aafd0236471ac9018671ca49",
                "fine_ids": []
            }
        }
    ],
    "paging": {
        "next": "https://merchant.hopscotch.in/api/order/multi-get?start=121&limit=20&access_token=8f937c7c6cea4f8c89f6428444edb178&since=2018-04-20",
        "previous": "https://merchant.hopscotch.in/api/order/multi-get?start=81&limit=20&access_token=8f937c7c6cea4f8c89f6428444edb178&since=2018-04-20"
    }
}
```

Returns all orders that have changed state since the date and time requested. Use this API to keep your orders processing system in sync with Hopscotch. This API takes a parameter 'since' and returns all orders that were updated since this time.

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/order/multi-get

<b>Parameteres</b>
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
			<b>optional</b> A limit on the number of products that can be returned. Limit can range from 1 to 500 items and the default is 50
		</td>
	</tr>
	<tr>
		<td>
			<b>since</b>
		</td>
		<td>
			<b>optional</b> Collect all the orders that have been updated since the time value passed into this parameter (UTC). Fetches from beginning of time if not specified. We accept 2 formats, one with precision down to day and one with precision down to seconds. Example: Jan 20th, 2014 is 2014-01-20, Jan 20th, 2014 20:10:20 is 2014-01-20T20:10:20.
		</td>
	</tr>
</table>

<b>Returns</b></br>
This API returns all the orders that have been updated since the datetime from the 'since' parameter (UTC) ordered by order time starting with the offset 'start' up to the parameter 'limit.' For example, if there are 1000 orders since May 1, 2013 and start is 100, while limit is 50, this API will return the 100th order to the 149th order.

## Retrieve Unfulfilled Orders
> Example</br>
Assume your access token is "an_example_access_token" . If you want to get all the orders which still require fulfillment in pages of 100: </br></br>
start = 0 </br>
limit = 100 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/order/get-fulfill?start=0&limit=100&access_token=an_example_access_token
```

> Example Response

```json
{'code': 0,
 'data': [{'Order': {'ShippingDetail': {
                      "phone_number": "+86 13816792755",
                      "city": "Shanghai",
                      "state": "Shanghai",
                      "name": "EPC Shanghai - 088220",
                      "country": "CN",
                      "zipcode": "201901",
                      "street_address1": "No.419 Gongyue RD Baoshan District Shanghai - 088220"
                      },
                      'last_updated': '2014-01-20T20:20:20',
                      'order_time': '2014-01-20T20:20:20',
                      'released_to_merchant_time': '2014-01-20T21:20:20',
                      'order_id': '123456789009876543210164',
                      'order_total': '17.6',
                      'product_id': '10101',
                      'buyer_id': '1234fad43deaf71536cb2c74',
                      'quantity': '2',
                      'price':'8',
                      'cost':u’6.8',
                      'shipping':'2.35',
                      'shipping_cost':'2',
                      'product_name':'Dandelion Necklace',
                      'product_image_url':'http://d1zog42tnv26ho.cloudfront.net/4fea11fac43bf532f4001419-normal.jpg',
                      'days_to_fulfill': '2',
                      'hours_to_fulfill': '49',
                      'sku': 'Dandelion Necklace',
                      'state': 'APPROVED',
                      'transaction_id': '11114026a99e980d4e500269',
                      'variant_id': '1111fad63deaf71536cb2c76',
                      'is_combined_order': False,
                      'fine_ids': []}},
           {'Order': {'ShippingDetail': {
                        "phone_number": "+86 13816792755",
                        "city": "Shanghai",
                        "state": "Shanghai",
                        "name": "EPC Shanghai - 088220",
                        "country": "CN",
                        "zipcode": "201901",
                        "street_address1": "No.419 Gongyue RD Baoshan District Shanghai - 088220"
                        },
                       'last_updated': '2014-01-20T20:20:20',
                       'order_time': '2014-01-20T20:20:20',
                       'released_to_merchant_time': '2014-01-20T21:20:20',
                       'order_id': '1114a7cfb2ec2d42d272b627',
                       'order_total': '17.6',
                      'product_id': '101012',
                      'buyer_id': '1234fad43deaf71536cb2c74',
                      'quantity': '2',
                      'price':'8',
                      'cost':'6.8',
                      'shipping':'2.35',
                      'shipping_cost':'2',
                      'product_name':'Dandelion Necklace',
                      'product_image_url':'http://d1zog42tnv26ho.cloudfront.net/4fea11fac43bf532f4001419-normal.jpg',
                      'days_to_fulfill': '2',
                      'hours_to_fulfill': '49',
                      'sku': 'Dandelion Necklace',
                      'state': 'APPROVED',
                      'transaction_id': '11114026a99e980d4e500269',
                      'variant_id': '1111fad63deaf71536cb2c76',
                      'is_combined_order': False,
                      'fine_ids': []}}],
 'message': '',
 'paging': {'next': 'https://merchant.hopscotch.in/api/order/get-fulfill?start=100&limit=100&access_token=an_example_access_token'}
 }
```

Returns all orders that currently require fulfillment. This API takes no parameters but may require pagination if the number of orders is too large.

<b>HTTP Request Type: GET</b>

<b>Definition</b></br>
GET https://merchant.hopscotch.in/api/order/get-fulfill

<b>Parameteres</b>
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
			<b>optional</b> A limit on the number of products that can be returned. Limit can range from 1 to 500 items and the default is 50
		</td>
	</tr>
	<tr>
		<td>
			<b>since</b>
		</td>
		<td>
			<b>optional</b> Collect all the orders that have been updated since the time value passed into this parameter (UTC). Fetches from beginning of time if not specified. We accept 2 formats, one with precision down to day and one with precision down to seconds. Example: Jan 20th, 2014 is 2014-01-20, Jan 20th, 2014 20:10:20 is 2014-01-20T20:10:20.
		</td>
	</tr>
</table>

<b>Returns</b></br>
Returns a list of all order that currently require fulfillment that's updated since 'since' (UTC). If the list of orders is longer than 'limit' the results will require pagination.

## Fulfill an Order
> Example</br>
Assume your access token is "an_example_access_token" . Use this if you have shipped an order to a user and would like to mark it shipped on Hopscotch. If the order's order_id is "098765432112345678901234",the tracking number is "12345679" and the provider is USPS: </br></br>
id = 098765432112345678901234 </br>
tracking_provider = USPS </br>
tracking_number = 12345678 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/order/fulfill-one -d "tracking_provider=USPS&tracking_number=12345679&id=098765432112345678901234&access_token=an_example_access_token"
```

> Example Response

```json
{
    'code': 0,
    'data': {'success': True},
    'message': 'Your order is been processed right now!'
}
```

Call this API once you have shipped the item to the recipient. 

<b>HTTP Request Type: POST</b>

<b>Definition</b></br>
POST https://merchant.hopscotch.in/api/order/fulfill-one

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>id</b>
		</td>
		<td>
			Hopscotch's unique identifier for the order, or 'order_id' in the Order object
		</td>
	</tr>
	<tr>
		<td>
			<b>tracking_provider</b>
		</td>
		<td>
			The carrier that will be shipping your package to its destination
		</td>
	</tr>
	<tr>
		<td>
			<b>tracking_number</b>
		</td>
		<td>
			<b>optional</b> The unique identifier that your carrier provided so that the user can track their package as it is being delivered. Tracking number should only contain alphanumeric characters with no space between them.
		</td>
	</tr>
	<tr>
		<td>
			<b>ship_note</b>
		</td>
		<td>
			<b>optional</b> A note to yourself when you marked the order as shipped
		</td>
	</tr>
</table>

<b>Returns</b></br>
If the order is in the 'APPROVED' state, the order is not already fulfilled and all the parameters are correct, the API will mark the order as shipped and return a HTTP status code of 200.

## Refund/Cancel an Order
> Example</br>
Assume your access token is "an_example_access_token" . If you want to refund the order with order_id "098765432112345678901234" because you are out of inventory. </br> </br>
id = 098765432112345678901234 </br>
reason_code = 18 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/order/refund -d "reason_code=18&id=098765432112345678901234&access_token=an_example_access_token"
```

> Example Response

```json
{
    'code': 0,
    'data': {'success': True},
    'message': ''
}
```

Call this API if you cannot fulfill the order for any reason. 

<b>HTTP Request Type: POST</b>

<b>Definition</b></br>
POST https://merchant.hopscotch.in/api/order/refund

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>id</b>
		</td>
		<td>
			Hopscotch's unique identifier for the order, or 'order_id' in the Order object
		</td>
	</tr>
	<tr>
		<td>
			<b>reason_code</b>
		</td>
		<td>
			An integer representing the reason for the refund. Check the table between for accepted reason codes
		</td>
	</tr>
	<tr>
		<td>
			<b>reason_note</b>
		</td>
		<td>
			<b>optional</b> A note to the user explaining reason for the refund. This field is required if reason_code is -1(Other)
		</td>
	</tr>
</table>

<b>Refund Reason Codes -- All Orders</b>
<table>
	<tr>
		<td>
			<b>-1</b>
		</td>
		<td>
			Other
		</td>
	</tr>
	<tr>
		<td>
			<b>18</b>
		</td>
		<td>
			Placed order by mistake
		</td>
	</tr>
	<tr>
		<td>
			<b>20</b>
		</td>
		<td>
			Shipping taking too long
		</td>
	</tr>
	<tr>
		<td>
			<b>22</b>
		</td>
		<td>
			Item does not fit
		</td>
	</tr>
	<tr>
		<td>
			<b>23</b>
		</td>
		<td>
			Received the wrong item
		</td>
	</tr>
	<tr>
		<td>
			<b>24</b>
		</td>
		<td>
			Item is counterfeit
		</td>
	</tr>
	<tr>
		<td>
			<b>25</b>
		</td>
		<td>
			Item is damaged
		</td>
	</tr>
	<tr>
		<td>
			<b>26</b>
		</td>
		<td>
			Item does not work as described
		</td>
	</tr>
	<tr>
		<td>
			<b>27</b>
		</td>
		<td>
			Item does not match listing
		</td>
	</tr>
	<tr>
		<td>
			<b>30</b>
		</td>
		<td>
			Item delivered to wrong address
		</td>
	</tr>
	<tr>
		<td>
			<b>31</b>
		</td>
		<td>
			Customer provided the wrong address
		</td>
	</tr>
	<tr>
		<td>
			<b>32</b>
		</td>
		<td>
			Item was returned to sender
		</td>
	</tr>
	<tr>
		<td>
			<b>33</b>
		</td>
		<td>
			Incomplete Order
		</td>
	</tr>
	<tr>
		<td>
			<b>34</b>
		</td>
		<td>
			Store is unable to fulfill order
		</td>
	</tr>
	<tr>
		<td>
			<b>35</b>
		</td>
		<td>
			Item marked delivered but user did not receive it
		</td>
	</tr>
	<tr>
		<td>
			<b>38</b>
		</td>
		<td>
			Replacement item shipment beyond latest delivery date
		</td>
	</tr>
	<tr>
		<td>
			<b>1001</b>
		</td>
		<td>
			Received the wrong color
		</td>
	</tr>
	<tr>
		<td>
			<b>1002</b>
		</td>
		<td>
			Item is of poor quality
		</td>
	</tr>
	<tr>
		<td>
			<b>1004</b>
		</td>
		<td>
			Product listing is missing information
		</td>
	</tr>
	<tr>
		<td>
			<b>1005</b>
		</td>
		<td>
			Item did not meet expectations
		</td>
	</tr>
	<tr>
		<td>
			<b>1006</b>
		</td>
		<td>
			Package was empty
		</td>
	</tr>
</table>

<b>Refund Reason Codes -- Unfulfilled Orders Only</b></br>
<table>
	<tr>
		<td>
			<b>1</b>
		</td>
		<td>
			Store is unable to fulfill order
		</td>
	</tr>
</table>

<b>Returns</b></br>
If the order is not already refunded and all the parameters are correct, the API will mark the order as refunded and return a HTTP status code of 200.

## Modify Tracking of a Shipped Order
> Example</br>
Assume your access token is "an_example_access_token" . Suppose you want to update the order with order_id "098765432112345678901234" to have tracking_provider of 'USPS' and tracking number of "12345678": </br>
id = 098765432112345678901234 </br>
tracking_provider = USPS </br>
tracking_number = 12345678 </br>
access_token = an_example_access_token

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/order/modify-tracking -d "tracking_provider=USPS&tracking_number=12345678&id=098765432112345678901234&access_token=an_example_access_token"
```

> Example Response

```json
{
    'code': 0,
    'data': {'success': True},
    'message': ''
}
```

Update tracking information about an order. Call this to change the tracking number or provider for an order that has already been marked shipped.

<b>HTTP Request Type: POST</b>

<b>Definition</b></br>
POST https://merchant.hopscotch.in/api/order/modify-tracking

<b>Parameters</b>
<table>
	<tr>
		<td>
			<b>id</b>
		</td>
		<td>
			Hopscotch's unique identifier for the order, or 'order_id' in the Order object
		</td>
	</tr>
	<tr>
		<td>
			<b>tracking_provider</b>
		</td>
		<td>
			The carrier that will be shipping your package to its destination
		</td>
	</tr>
	<tr>
		<td>
			<b>tracking_number</b>
		</td>
		<td>
			<b>optional</b> The unique identifier that your carrier provided so that the user can track their package as it is being delivered. Tracking number should only contain alphanumeric characters with no space between them.
		</td>
	</tr>
	<tr>
		<td>
			<b>ship_note</b>
		</td>
		<td>
			<b>optional</b> A note to yourself when you marked the order as shipped
		</td>
	</tr>
</table>

<b>Returns</b></br>
If the order is in the SHIPPED state, and all the parameters are correct, the API will update the tracking information of that order and return a HTTP status code of 200.


