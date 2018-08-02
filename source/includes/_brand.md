# Brand
With this API you can create and update a brand.

<b>Attributes</b>
<table>
<tbody>
<tr>
<td><b>id</b></td>
<td>Brand Id an integer.</td>
</tr>
<tr>
<td><b>description</b></td>
<td>Description of the brand.</td>
</tr>
<tr>
<td><b>image_url</b></td>
<td>URL of image.</td>
</tr>
<tr>
<td><b>category</b></td>
<td>Hopscotch defined Category to which brand is associated.</td>
</tr>
<tr>
<td><b>name</b></td>
<td>Brand name</td>
</tr>
<tr>
<td><b>short_name</b></td>
<td>Short name associated to brand</td>
</tr>
<tr>
<td><b>acronym</b></td>
<td>Brand acronym</td>
</tr>
<tr>
<td><b>on_label</b></td>
<td>A boolean field</td>
</tr>
<tr>
<td><b>bdm</b></td>
<td>BDM name</td>
</tr>
<tr>
<td><b>labelsTemplate</b></td>
<td></td>
</tr>
<tr>
<td><b>founderName</b></td>
<td></td>
</tr>
<tr>
<td><b>founderYear</b></td>
<td></td>
</tr>
<tr>
<td><b>squareImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>rectangleWebsiteImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>rectangleMobileImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>appSmallImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>appFlexiImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>listPreviewPage</b></td>
<td></td>
</tr>
<tr>
<td><b>image</b></td>
<td></td>
</tr>
<tr>
<td><b>locationImage</b></td>
<td></td>
</tr>
<tr>
<td><b>appImage</b></td>
<td></td>
</tr>
<tr>
<td><b>appFlexiImageShowInBoutique</b></td>
<td></td>
</tr>
<tr>
<td><b>saleplanName</b></td>
<td></td>
</tr>
<tr>
<td><b>saleplanDescription</b></td>
<td></td>
</tr>
<tr>
<td><b>storyImageWebsiteImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>websiteColor</b></td>
<td></td>
</tr>
<tr>
<td><b>storyImageMobileImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>mobileColor</b></td>
<td></td>
</tr>
</tbody>
</table>

## Create a Brand

Use below endpoint to create a new brand. </br>
<b>HTTP Request Type: POST</b>

<b>Definition</b> </br>
POST https://merchant.hopscotch.in/api/brand/add

<!-- 
	Existing Brand Creation JSON.
{
	"id": "",
	"imageId": "",
	"name": "Test 2 ",
	"description": "<p>asdfasfd</p>",
	"shortName": "TBDD",
	"labelsTemplate": "ListPreview",
	"founderName": "",
	"founderYear": "",
	"squareImageId": "",
	"rectangleWebsiteImageId": "",
	"rectangleMobileImageId": "",
	"appSmallImageId": "",
	"appFlexiImageId": "",
	"listPreviewPage": "27",
	"image": "",
	"locationImage": "",
	"appImage": "",
	"appFlexiImageShowInBoutique": "",
	"saleplanName": "",
	"saleplanDescription": "",
	"storyImageWebsiteImageId": "",
	"websiteColor": "",
	"storyImageMobileImageId": "",
	"mobileColor": "",
	"bdmIds": ["1"],
	"categoryIds": ["367"]
} -->

<b>Parameters</b>
<table>
<tbody>
<tr>
<td><b>id</b></td>
<td>Brand Id an integer.</td>
</tr>
<tr>
<td><b>description</b></td>
<td>Description of the brand.</td>
</tr>
<tr>
<td><b>image_url</b></td>
<td>URL of image.</td>
</tr>
<tr>
<td><b>category</b></td>
<td>Hopscotch defined Category to which brand is associated.</td>
</tr>
<tr>
<td><b>name</b></td>
<td>Brand name</td>
</tr>
<tr>
<td><b>short_name</b></td>
<td>Short name associated to brand</td>
</tr>
<tr>
<td><b>acronym</b></td>
<td>Brand acronym</td>
</tr>
<tr>
<td><b>on_label</b></td>
<td>A boolean field</td>
</tr>
<tr>
<td><b>bdm</b></td>
<td>BDM name</td>
</tr>
<tr>
<td><b>labelsTemplate</b></td>
<td></td>
</tr>
<tr>
<td><b>founderName</b></td>
<td></td>
</tr>
<tr>
<td><b>founderYear</b></td>
<td></td>
</tr>
<tr>
<td><b>squareImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>rectangleWebsiteImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>rectangleMobileImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>appSmallImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>appFlexiImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>listPreviewPage</b></td>
<td></td>
</tr>
<tr>
<td><b>image</b></td>
<td></td>
</tr>
<tr>
<td><b>locationImage</b></td>
<td></td>
</tr>
<tr>
<td><b>appImage</b></td>
<td></td>
</tr>
<tr>
<td><b>appFlexiImageShowInBoutique</b></td>
<td></td>
</tr>
<tr>
<td><b>saleplanName</b></td>
<td></td>
</tr>
<tr>
<td><b>saleplanDescription</b></td>
<td></td>
</tr>
<tr>
<td><b>storyImageWebsiteImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>websiteColor</b></td>
<td></td>
</tr>
<tr>
<td><b>storyImageMobileImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>mobileColor</b></td>
<td></td>
</tr>
</tbody>
</table>

<b>Returns</b>

## Update a Brand

Updates the specified brand with the parameters passed in the request. Any attribute not provided will be left unchanged. For example, if you pass the name parameter we will update the name of the brand and leave everything else unchanged.</br>

<b>HTTP Request Type: POST</b>

<b>Definition</b>
POST https://merchant.hopscotch.in/api/brand/update

<b>Parameters</b>
<table>
<tbody>
<tr>
<td><b>id</b></td>
<td>Brand Id an integer.</td>
</tr>
<tr>
<td><b>description</b></td>
<td>Description of the brand.</td>
</tr>
<tr>
<td><b>image_url</b></td>
<td>URL of image.</td>
</tr>
<tr>
<td><b>category</b></td>
<td>Hopscotch defined Category to which brand is associated.</td>
</tr>
<tr>
<td><b>name</b></td>
<td>Brand name</td>
</tr>
<tr>
<td><b>short_name</b></td>
<td>Short name associated to brand</td>
</tr>
<tr>
<td><b>acronym</b></td>
<td>Brand acronym</td>
</tr>
<tr>
<td><b>on_label</b></td>
<td>A boolean field</td>
</tr>
<tr>
<td><b>bdm</b></td>
<td>BDM name</td>
</tr>
<tr>
<td><b>labelsTemplate</b></td>
<td></td>
</tr>
<tr>
<td><b>founderName</b></td>
<td></td>
</tr>
<tr>
<td><b>founderYear</b></td>
<td></td>
</tr>
<tr>
<td><b>squareImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>rectangleWebsiteImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>rectangleMobileImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>appSmallImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>appFlexiImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>listPreviewPage</b></td>
<td></td>
</tr>
<tr>
<td><b>image</b></td>
<td></td>
</tr>
<tr>
<td><b>locationImage</b></td>
<td></td>
</tr>
<tr>
<td><b>appImage</b></td>
<td></td>
</tr>
<tr>
<td><b>appFlexiImageShowInBoutique</b></td>
<td></td>
</tr>
<tr>
<td><b>saleplanName</b></td>
<td></td>
</tr>
<tr>
<td><b>saleplanDescription</b></td>
<td></td>
</tr>
<tr>
<td><b>storyImageWebsiteImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>websiteColor</b></td>
<td></td>
</tr>
<tr>
<td><b>storyImageMobileImageUrl</b></td>
<td></td>
</tr>
<tr>
<td><b>mobileColor</b></td>
<td></td>
</tr>
</tbody>
</table>

<b>Returns</b>
If the request was successful the API will return an HTTP status code of 200 and a status code of 0.