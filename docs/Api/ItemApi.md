# Swagger\Client\ItemApi

All URIs are relative to *https://api.ebay.com{basePath}*

Method | HTTP request | Description
------------- | ------------- | -------------
[**getItemFeed**](ItemApi.md#getitemfeed) | **GET** /item | 

# **getItemFeed**
> \Swagger\Client\Model\ItemResponse getItemFeed($x_ebay_c_marketplace_id, $range, $feed_scope, $category_id, $date)



This method lets you download a TSV_GZIP (tab separated value gzip) Item feed file. The feed file contains all the items from all the child categories of the specified category. The first line of the file is the header, which labels the columns and indicates the order of the values on each line. Each header is described in the Response fields section. There are two types of item feed files generated: A daily Item feed file containing all the newly listed items for a specific category, date, and marketplace (feed_scope = NEWLY_LISTED) A weekly Item Bootstrap feed file containing all the items in a specific category and marketplace (feed_scope = ALL_ACTIVE) Note: Filters are applied to the feed files. For details, see Feed File Filters. When curating the items returned, be sure to code as if these filters are not applied as they can be changed or removed in the future. URLs for this method Production URL: https://api.ebay.com/buy/feed/v1_beta/ Sandbox URL: https://api.sandbox.ebay.com/buy/feed/v1_beta/ Downloading feed files Item feed files are binary gzip files. If the file is larger than 100 MB, the download must be streamed in chunks. You specify the size of the chunks in bytes using the Range request header. The Content-range response header indicates where in the full resource this partial chunk of data belongs and the total number of bytes in the file. For more information about using these headers, see Retrieving a gzip feed file. In addition to the API, there is an open source Feed SDK written in Java that downloads, combines files into a single file when needed, and unzips the entire feed file. It also lets you specify field filters to curate the items in the file. Note: The response is always a TSV_GZIP file. However for documentation purposes, the response is shown as JSON fields so that the value returned in each column can be explained. The order of the response fields, shows you the order of the columns in the feed file. Restrictions For a list of supported sites and other restrictions, see API Restrictions.

### Example
```php
<?php
require_once(__DIR__ . '/vendor/autoload.php');

// Configure OAuth2 access token for authorization: api_auth
$config = Swagger\Client\Configuration::getDefaultConfiguration()->setAccessToken('YOUR_ACCESS_TOKEN');

$apiInstance = new Swagger\Client\Api\ItemApi(
    // If you want use custom http client, pass your client which implements `GuzzleHttp\ClientInterface`.
    // This is optional, `GuzzleHttp\Client` will be used as default.
    new GuzzleHttp\Client(),
    $config
);
$x_ebay_c_marketplace_id = "x_ebay_c_marketplace_id_example"; // string | The ID of the eBay marketplace where the item is hosted. Note: This value is case sensitive. For example: &nbsp;&nbsp;X-EBAY-C-MARKETPLACE-ID = EBAY_US For a list of supported sites see, API Restrictions.
$range = "range_example"; // string | This header specifies the range in bytes of the chunks of the gzip file being returned. Format: bytes=startpos-endpos For example, the following retrieves the first 10 MBs of the feed file. &nbsp;&nbsp;Range bytes=0-10485760 For more information about using this headers, see Retrieving a gzip feed file. Maximum: 100 MB (10MB in the Sandbox)
$feed_scope = "feed_scope_example"; // string | Specifies the type of feed file to return. Valid Values: NEWLY_LISTED - Returns the daily Item feed file containing all Good 'Til Cancelled items that were listed on the day specified by the date parameter in the category specified by the category_id parameter. /item?feed_scope=NEWLY_LISTED&amp;category_id=15032&amp;date=20170925 ALL_ACTIVE - Returns the weekly Item Bootstrap feed file containing all the Good 'Til Cancelled items in the category specified by the category_id parameter. Note: Bootstrap files are generated every Tuesday and the file is available on Wednesday. However, the exact time the file is available can vary so we recommend you download the Bootstrap file on Thursday. The items in the file are the items that were in the specified category on Sunday. /item?feed_scope=ALL_ACTIVE&amp;category_id=15032
$category_id = "category_id_example"; // string | An eBay top-level category ID of the items to be returned in the feed file. The list of eBay category IDs changes over time and category IDs are not the same across all the eBay marketplaces. To get a list of the top-level categories for a marketplaces, you can use the Taxonomy API getCategoryTree method. This method retrieves the complete category tree for the marketplace. The top-level categories are identified by the categoryTreeNodeLevel field. For example: &nbsp;&nbsp;&quot;categoryTreeNodeLevel&quot;: 1 For details see Get Categories for Buy APIs. Restriction: Must be a top-level (L1) category
$date = "date_example"; // string | The date of the daily Item feed file (feed_scope=NEWLY_LISTED) you want. The date is required only for the daily Item feed file. If you specify a date for the Item Bootstrap file (feed_scope=ALL_ACTIVE), the date is ignored and the latest file is returned. The date the Item Bootstrap feed file was generated is returned in the Last-Modified response header. The Item feed files are generated every day and there are 14 daily files available. Note: The daily Item feed files are available each day after 9AM MST (US Mountain Standard Time), which is -7 hours UTC time. There is a 48 hour latency when generating the Item feed files. This means you can download the file for July 10th on July 12 after 9AM MST. Note: For categories with a large number of items, the latency can be up to 72 hours. Format: yyyyMMdd Requirements: Required when feed_scope=NEWLY_LISTED Must be within 3-14 days in the past

try {
    $result = $apiInstance->getItemFeed($x_ebay_c_marketplace_id, $range, $feed_scope, $category_id, $date);
    print_r($result);
} catch (Exception $e) {
    echo 'Exception when calling ItemApi->getItemFeed: ', $e->getMessage(), PHP_EOL;
}
?>
```

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **x_ebay_c_marketplace_id** | **string**| The ID of the eBay marketplace where the item is hosted. Note: This value is case sensitive. For example: &amp;nbsp;&amp;nbsp;X-EBAY-C-MARKETPLACE-ID &#x3D; EBAY_US For a list of supported sites see, API Restrictions. |
 **range** | **string**| This header specifies the range in bytes of the chunks of the gzip file being returned. Format: bytes&#x3D;startpos-endpos For example, the following retrieves the first 10 MBs of the feed file. &amp;nbsp;&amp;nbsp;Range bytes&#x3D;0-10485760 For more information about using this headers, see Retrieving a gzip feed file. Maximum: 100 MB (10MB in the Sandbox) |
 **feed_scope** | **string**| Specifies the type of feed file to return. Valid Values: NEWLY_LISTED - Returns the daily Item feed file containing all Good &#x27;Til Cancelled items that were listed on the day specified by the date parameter in the category specified by the category_id parameter. /item?feed_scope&#x3D;NEWLY_LISTED&amp;amp;category_id&#x3D;15032&amp;amp;date&#x3D;20170925 ALL_ACTIVE - Returns the weekly Item Bootstrap feed file containing all the Good &#x27;Til Cancelled items in the category specified by the category_id parameter. Note: Bootstrap files are generated every Tuesday and the file is available on Wednesday. However, the exact time the file is available can vary so we recommend you download the Bootstrap file on Thursday. The items in the file are the items that were in the specified category on Sunday. /item?feed_scope&#x3D;ALL_ACTIVE&amp;amp;category_id&#x3D;15032 |
 **category_id** | **string**| An eBay top-level category ID of the items to be returned in the feed file. The list of eBay category IDs changes over time and category IDs are not the same across all the eBay marketplaces. To get a list of the top-level categories for a marketplaces, you can use the Taxonomy API getCategoryTree method. This method retrieves the complete category tree for the marketplace. The top-level categories are identified by the categoryTreeNodeLevel field. For example: &amp;nbsp;&amp;nbsp;&amp;quot;categoryTreeNodeLevel&amp;quot;: 1 For details see Get Categories for Buy APIs. Restriction: Must be a top-level (L1) category |
 **date** | **string**| The date of the daily Item feed file (feed_scope&#x3D;NEWLY_LISTED) you want. The date is required only for the daily Item feed file. If you specify a date for the Item Bootstrap file (feed_scope&#x3D;ALL_ACTIVE), the date is ignored and the latest file is returned. The date the Item Bootstrap feed file was generated is returned in the Last-Modified response header. The Item feed files are generated every day and there are 14 daily files available. Note: The daily Item feed files are available each day after 9AM MST (US Mountain Standard Time), which is -7 hours UTC time. There is a 48 hour latency when generating the Item feed files. This means you can download the file for July 10th on July 12 after 9AM MST. Note: For categories with a large number of items, the latency can be up to 72 hours. Format: yyyyMMdd Requirements: Required when feed_scope&#x3D;NEWLY_LISTED Must be within 3-14 days in the past | [optional]

### Return type

[**\Swagger\Client\Model\ItemResponse**](../Model/ItemResponse.md)

### Authorization

[api_auth](../../README.md#api_auth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: text/tab-separated-values

[[Back to top]](#) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to Model list]](../../README.md#documentation-for-models) [[Back to README]](../../README.md)

