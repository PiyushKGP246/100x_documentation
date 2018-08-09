# Hopscotch OAUTH
## Overview
Your app cannot access Hopscotch data without authenticating itself first. Hopscotch uses the OAuth 2.0 specification to identify which apps are allowed access to resources. This guide will walk you through the authentication process.

## Terminology
Here's a list of terms you should be familiar with while reading this guide.
<ul>
<li><b>App</b>
<br/>
The app, or the client, is any application that would like to access a merchant's data on Hopscotch.<br/>
</li>
<li><b>User</b>
<br/>
The user is someone with a merchant account on Hopscotch. This is the person giving permission to the app to access their data.<br/>
</li>
<li><b>Access Token</b>
<br/>
The access token is the app's password that it uses to access users' data.<br/>
</li>
</ul>

## Step 1: Asking for Permission
The first step is to get permission from the user. Direct the user to this URL: </br>

`https://merchant.hopscotch.in/oauth/authorize?client_id={client_id}`

With {client_id} replaced by the your app's ID (without the braces). This will open up the page on the user's dashboard. The user must be logged in to their merchant account on Hopscotch to see this prompt.

## Step 2: Receiving the Authorization Code
After the user grants permission to your app, Hopscotch will redirect the user to the redirect URI specified when the app was created. One of the parameters of this request is the Authorization Code (without the braces). </br>

`https://example.redirect.uri.com?code={authorization_code}`

This authorization code can now be exchanged for an access token.

Please note the authorization code will expire after 5 minutes and can only be used once.

## Step 3: Obtaining the Access Token
> Example</br>
Assume your client id was 55c277347770e02e65d4cd83, your client_secret was 123456789012345678901234, your redirect uri was https://example.com and your authorization code was 111222333444555666. </br>

> Example Request

```curl
> curl https://merchant.wish.com/api/oauth/access_token -d "client_id=55c277347770e02e65d4cd83&client_secret=123456789012345678901234&code=111222333444555666&redirect_uri=https%3A%2F%2Fexample.com&grant_type=authorization_code"
```

> Example Response

```json
{
    'message' : '',
    'code' : 0,
    'data' : { 'access_token' : '1qaz2wsx3edc4rfv5tgb',
               'refresh_token' : 'mju7nhy6bgt5vfr4cde3',
               'expires_in' : 86400,
               'expiry_time' : 1438922740,
               'expiry_string': '2015-08-07 04:45:40 UTC'
             }
}
```

To obtain an access token, your app must make the following request:

`POST https://merchant.hopscotch.in/api/oauth/access_token`

<b>Parameters</b>
<table>
	<tr>
		<td>
			client_id
		</td>
		<td>
			Your app's client ID
		</td>
	</tr>
	<tr>
		<td>
			client_secret
		</td>
		<td>
			Your app's client secret
		</td>
	</tr>
	<tr>
		<td>
			code
		</td>
		<td>
			The authorization code you received
		</td>
	</tr>
	<tr>
		<td>
			grant_type
		</td>
		<td>
			The string 'authorization_code'
		</td>
	</tr>
	<tr>
		<td>
			redirect_uri
		</td>
		<td>
			Your app's redirect uri that you specified when you created the app
		</td>
	</tr>
</table>

Hopscotch will respond with an access token and a refresh token. Your app should store both these tokens somewhere. The access token is used to make authorized requests, and the refresh token is used to obtain new access tokens. Hopscotch will also respond with a merchant user ID, which uniquely identifies the user that authorized your client.

For security, our access tokens are temporary, and will expire after 30 days. To obtain a new access token, see Step 5 of this guide.

## Step 4: Making Authorized Requests
To make an authorized request, add the following to the request header:

`Authorization: Bearer {access_token}`

Alternatively, you can also add the access token as a parameter in the body of a request. For example, you can use the following endpoint to test your access token:

`POST https://merchant.hopscotch.in/api/auth_test`

<b>Parameters</b>
<table>
	<tr>
		<td>
			access_token
		</td>
		<td>
			Your access token
		</td>
	</tr>
</table>

## Step 5: Obtaining New Access Tokens
> Example</br>
Assume your client id was 55c277347770e02e65d4cd83, your client_secret was 123456789012345678901234, and your refresh token was mju7nhy6bgt5vfr4cde3.</br>

> Example Request

```curl
> curl https://merchant.hopscotch.in/api/oauth/refresh_token -d "client_id=55c277347770e02e65d4cd83&client_secret=123456789012345678901234&refresh_token=mju7nhy6bgt5vfr4cde3&grant_type=refresh_token"
```

> Example Response

```json
{
    'message' : '',
    'code' : 0,
    'data' : { 'access_token' : '1qaz2wsx3edc4rfv5tgb',
               'refresh_token' : 'mju7nhy6bgt5vfr4cde3',
               'expires_in' : 86400,
               'expiry_time' : 1438922740,
               'expiry_string': '2015-08-07 04:45:40 UTC'
             }
}
```

Access tokens expire after a certain period of time. In order to obtain a new access token without going through the full oAuth process again, your app can make the following request:

`POST https://merchant.hopscotch.in/api/oauth/refresh_token`

<b>Parameters</b>
<table>
	<tr>
		<td>
			client_id
		</td>
		<td>
			Your app's client ID
		</td>
	</tr>
	<tr>
		<td>
			client_secret
		</td>
		<td>
			Your app's client secret
		</td>
	</tr>
	<tr>
		<td>
			refresh_token
		</td>
		<td>
			Your refresh token
		</td>
	</tr>
	<tr>
		<td>
			grant_type
		</td>
		<td>
			The string 'refresh_token'
		</td>
	</tr>
</table>

Please note that your existing access token will be revoked.