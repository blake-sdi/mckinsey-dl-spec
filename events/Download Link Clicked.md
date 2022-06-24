# Download Link Clicked

Download link clicks will be automatically detected by comparing the href of the link clicked to a predefined list of file extensions. This spec is for manually firing download links if necessary, such as for a button that asynchronously generates the file that will be downloaded using an onClick event.

## Data Attributes HTML Code

```html
  <a href="<linkDestination>" 
    data-layer-event-prefix="Download Link"
    data-layer-action="click"
    data-layer-category="<category>"
    data-layer-subcategory="<subcategory?>"
    data-layer-subcategory2="<subcategory2?>"
    data-layer-text="<text?>"

    data-layer-file-name="<fileName>" 
    data-layer-report-name="<reportName>"
    data-layer-report-type="<fileType>"
  >
```
Items with a ? are optional

## Generated Javascript Code

```js
window.appEventData = window.appEventData || [];
appEventData.push({
  "event": "Download Link Clicked",
  "linkInfo": {
    "category": "<category?>",
    "subcategory": "<subcategory?>",
    "subcategory2": "<subcategory2?>",
    "fileName": "<fileName>",
    "linkRegion": "<linkRegion?>",
    "reportName": "<reportName>"
    "reportType": "<fileType>",
    "text": "<text>",
  }
});
```
Items with a ? may not be generated depending on what attributes are present and the ancestry of the clicked item.

## Variable Definitions

|Field|Type|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|category|string|Category of the link|chat, ecommerce, learn more, share, subscribe, visit|
|subcategory|string|Subcategory of the link|buy now, email, print, social|
|subcategory2|string|Subcategory tier 2 of the link. Often used for service names, such as with a share > social.|facebook, twitter|
|fileName|string|Indicates the filename for download link tracking. Derived from the anchor href attribute|Year End 2012.pdf, Operating Instructions.doc|
|regions|string|Pipe-delimited list of all regions in ancestry of clicked item. Automatically generated.|
|text|string|Text contents of the item clicked on, or an alternative text label to use instead|Download File|
|reportName|string|Name of a downloaded file as specified by McKinsey|meet-the-next-normal-consumer|
|reportType|string|Type of a downloaded file. Not the file extension, but rather custom types provided by the site.|pdf, article|
