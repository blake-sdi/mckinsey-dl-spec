# UI Item Clicked

These HTML attributes should be added to items that do not qualify as CTAs, but that still need to be tracked. Examples include expanding a UI accordion, clicking on a tab, or clicking on an interactive component.

## Data Attributes HTML Code

```html
  <a href="<linkDestination>"
    data-layer-linkInfo-eventPrefix="UI Item"
    data-layer-linkInfo-action="click"
    data-layer-linkInfo-category="<category>"
    data-layer-linkInfo-subcategory="<subcategory?>"
    data-layer-linkInfo-text="<text?>"
  >
```

Items with a ? are optional

## Generated Javascript Code

```js
window.appEventData = window.appEventData || [];
appEventData.push({
  "event": "CTA Link Clicked",
  "linkInfo": {
    "category": "<category>",
    "subcategory": "<subcategory>"
    "region": "<region?>",
    "text": "<text>",
  }
});
```

Items with a ? may not be generated depending on what attributes are present and the ancestry of the clicked item.

### Variable Definitions

|Field|Type|Description|Example|Pattern|Min Length|Max Length|Minimum|Maximum|Multiple Of|
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|category|string|Additional subtype of the CTA|facebook|
|region|string|Pipe-delimited list of all regions in ancestry of clicked item. Automatically generated.|
|subcategory|string|Subcategory of the exit link|chat, social, buy now|
|text|string|Text contents of the item clicked on, or an alternative text label to use instead|Chat with us, Visit our Twitter Page|