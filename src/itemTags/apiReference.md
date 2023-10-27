# API Reference
You can interact with the API by using the following methods:

_Note that you can use tags for any Object that has flag support, but you should not do it with objects that are not supported_

### Usage Example
Imagine you want to check if a item has the `metal` tag set.
```js
if (ItemTags.Check(game.items.get("<id>"), ['metal'])) {
    console.log('The tag is set');
} else {
    console.log('The tag is not set');
}
```

### Get Tags
```js
ItemTags.Get(document);
```
- `document` - Any type of document that is [supported]()

Returns a `array` containing all the tags. If no tags are found then it returns `undefined`.

### Check Tags
```js
ItemTags.Check(document, tags);
```
- `document` - Any type of document that is [supported]()
- `tags` - A `string array` that defines the tags

Returns `true` if the document contains **all** the tags, otherwise returns `false`.

### Set the Tags
```js
ItemTags.Set(document, tags);
```
- `document` - Any type of document that is [supported]()
- `tags` - A `string array` that define the tags

Set the tags of a document.

### Add Tags
```js
ItemTags.Add(document, tags);
```
- `document` - Any type of document that is [supported]()
- `tags` - A `string array` that defines the tags

Append the tags to the already existing ones.

### Remove Tags
```js
ItemTags.Remove(document, tags);
```
- `document` - Any type of document that is [supported]()
- `tags` - A `string array` that defines the tags

Remove the tags from a document if they exist, otherwise does nothing.

### Clear Tags
```js
ItemTags.Clear(document);
```
Removes all tags from a document.

### Search Tags
```js
ItemTags.Search(tags);
```
- `tags` - A `string array` that defines the tags

Search your entire world for tags (does not search the compendium packs). Only the documents that contain **all** the passed tags are returned. The returned data looks like this:
```js
result: {
    actors: [] // A array containing all actors that have the tags
    items: [] // A array containing all items that have the tags
    noneFound: true // Will only be set when no documents match the search
}
```
