# API Reference
## Introduction
The Hopscotch merchant platform is an ecommerce platform. It allows merchants to upload and manage inventory for sale on Hopscotch. The platform is intended to be full-featured so merchants can manage their inventory, fulfill orders.

This API is intended to be a fully programmable alternative to the GUI version of this platform. However, it is a work in progress and is constantly being updated with new features.

The best way to get started using this API is to read through this section and then visit the User Guide section. If you're too excited and need to start now please visit the Quick Start Guide.

## Date/Time Format
All dates and times in our API are always in UTC unless otherwise mentioned.

## Authentication
Hopscotch uses the OAuth 2.0 specification to authenticate your requests. For a detailed guide on how to authenticate, click here.

Every request will need to be authenticated with an access token. When making requests, provide the access token as a GET or POST request parameter:

<table>
<thead>
<tr>
<th>Parameter</th>
<th>Type</th>
<th>Example</th>
</tr>
</thead>
<tbody>
<tr>
<td>access_token</td>
<td></td>
<td>“1qaz2wsx3edc4rfv5tgb”</td>
</tr>
</tbody>
</table>

Alternatively, the access token can be included in the header in this format:

<b>"Authorization: Bearer {access_token}"</b>

Requests must be made over HTTPS. Any call made over HTTP will be rejected.

## Response Scheme
Every response returned from the Wish API will have the same schema. This schema is intended to give you a predictable manner to check the status of your request and know where to get the data. Each response will have the following top level attributes: code, data, message, and sometimes paging.

<b>Attributes</b>
<table>
<tbody>
<tr>
<td><b>Code</b></td>
<td>Contains the status code for the request, 0 means success and any other number implies a failure.</td>
</tr>
<tr>
<td><b>Data</b></td>
<td>This attribute will store the response data that was requested.</td>
</tr>
<td><b>Message</b></td>
<td>Sometimes will store a human readable status message to aid in debugging. It is generally used only for errors.</td>
</tr>
<tr>
<td><b>Paging</b></td>
<td>If the number of results exceeds the limit for the request, this parameter will aid the client in paging to collect all the results.</td>
</tr>
</tbody>
</table>

## API Errors
The Wish API returns specific error data back to the client in the event of an error. Each error will contain the following data: 'code', 'message', 'data', and 'type'. Please see table below for descriptions of each attribute.

<b>Attributes</b>
<table>
<tbody>
<tr>
<td><b>Code</b></td>
<td>A unique number which represents the error that has occurred, example: 4001.</td>
</tr>
<tr>
<td><b>Type</b></td>
<td>A unique human readable representation of the error, example: not_found</td>
</tr>
<td><b>Message</b></td>
<td>A message describing the error that happened, example: "We could not find a product for id: 'aaa'"</td>
</tr>
<tr>
<td><b>Data</b></td>
<td>For most errors this will be empty.</td>
</tr>
</tbody>
</table>

## HTTP Status Codes
As well as using specific error codes in the event of an error, this API tries to conform to conventional HTTP response codes to indicate success or failure. Any response code of the form 2xx is generally considered successful. A status code of 4xx means that there was an error with the inputs. Any code in the 5xx range means that the server experienced an unexpected error and means we screwed up!

The HTTP status code should be used as a quick reference, but to get specific details please refer to the error code provided in the response.

## Pagination
For performance reasons it is necessary for this API to limit the number of results returned in each request. This limit varies per request, but there is always an upper bound on the number of items returned in any response. In the case that the number of results is too large, you may page through all the results with multiple requests.

If the results must be paginated the 'paging' attribute will exist in the response. This attribute will contain 'next' and 'prev' which are URLs for fetching the next or previous page of data.