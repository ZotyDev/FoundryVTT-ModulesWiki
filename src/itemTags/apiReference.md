# API Reference
You can interact with the API by using the following methods:

### Get Tags
```js
ItemTags.Get(document);
```
- `document` - Any type of document that is [supported]()

Returns a `array` containing all the tags. If no tags are found then it returns `undefined`.

### Check Tag
```js
ItemTags.Check(document, tag);
```
- `document` - Any type of document that is [supported]()
- `tag` - A `string` that defines the tag

Returns `true` if the document contains the tag, otherwise returns `false`.

### Set the Tags
```js
ItemTags.Set(document, tags);
```
- `document` - Any type of document that is [supported]()
- `tags` - A `array` of `strings` that define the tags

Set the tags of a document.

### Add Tag
```js
ItemTags.Add(document, tag);
```
- `document` - Any type of document that is [supported]()
- `tag` - A `string` that defines the tag

Adds a tag at the end of the already existing ones.

### Remove Tag
```js
ItemTags.Remove(document, tag);
```
- `document` - Any type of document that is [supported]()
- `tag` - A `string` that defines the tag

Removes a tag from a document if it exists, otherwise does nothing.

### Clear Tags
```js
ItemTags.Clear(document, tag);
```
Removes all tags from a document.
