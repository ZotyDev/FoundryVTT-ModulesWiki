# API Reference
You can interact with the API by using the following methods:

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
