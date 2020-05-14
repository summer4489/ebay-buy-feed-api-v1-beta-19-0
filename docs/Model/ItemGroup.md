# ItemGroup

## Properties
Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**item_group_id** | **string** | The unique identifier for the item group. This ID is returned in the primaryItemGroupId column of the Item Feed file. | [optional] 
**item_group_type** | **string** | The item group type. For example: SELLER_DEFINED_VARIATIONS, indicates that the item group was created by the seller. Code so that your app gracefully handles any future changes to this list. | [optional] 
**title** | **string** | The seller created title of the item group. This text is an escaped string when special characters are present, using the following rules: Double quotes (&amp;quot;) and backslashes (\\) in the Title are escaped with a backslash (\\) character If there are any tabs (\\t), double quotes (&amp;quot;), or backslashes (\\) in the Title, the entire Title will be wrapped in double quotes. For example Before: Misty Rainforest Modern Masters 2017 MTG Magic Fetch Land Free Ship W\\Tracking Marvel Legends HULK 8&amp;quot; Figure Avengers Age of Ultron Studios 6&amp;quot; Series After: &amp;quot;Misty Rainforest Modern Masters 2017 MTG Magic Fetch Land Free Ship W\\\\ Tracking&amp;quot; &amp;quot;Marvel Legends HULK 8\\&amp;quot; Figure Avengers Age of Ultron Studios 6\\&amp;quot; Series&amp;quot; | [optional] 
**varies_by_localized_aspects** | **string** | A pipe separated (|) list of the aspect (variation) names for this item group. The aspect name is BASE64 encoded. Note: This column can contain multiple values. &amp;nbsp;&amp;nbsp; Encoded Format: &amp;nbsp;&amp;nbsp;&amp;nbsp;aspectName|aspectName &amp;nbsp;&amp;nbsp; Encoded Example (The delimiters are emphasized): &amp;nbsp;&amp;nbsp;&amp;nbsp;Q29sb3I&#x3D;|U2l6ZQ&#x3D;&#x3D; &amp;nbsp;&amp;nbsp; Decoded: &amp;nbsp;&amp;nbsp;&amp;nbsp;Color|Size | [optional] 
**image_url** | **string** | The URL to the primary image of the item. The other images of the item group are returned in the additionalImageUrls column. | [optional] 
**additional_image_urls** | **string** | A pipe separated (|) list of URLs for the additional images for the item group. These images are in addition to the primary image, which is returned in the imageUrl column. Note: This column can contain multiple values. | [optional] 
**image_altering_prohibited** | **bool** | A boolean that indicates whether the images can be altered. If the value is true, you cannot modify the image. Note: Due to image licensing agreements and other legal concerns, modification (including resizing) of some images is strictly prohibited. These images are for display as-is only. | [optional] 

[[Back to Model list]](../../README.md#documentation-for-models) [[Back to API list]](../../README.md#documentation-for-api-endpoints) [[Back to README]](../../README.md)

