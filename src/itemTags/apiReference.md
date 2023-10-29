# API Reference

**!!Tags are case-sensitive!! Don't forget about it while using the API**

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
_⚠️ DEPRECATED ⚠️ - Please use [`SearchAll()`](#search-all)_
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

### Search All
```js
ItemTags.SearchAll(options);
```
- `options` - A `Object` that defines the options for the search
  - `method` (optional) - A `string` that defines what filtering method will be used when `tags` or `string` is passed, this value can be:
    - `'includeAND'`
      - For tags: only shows results that contain **all** the passed tags
      - For string: only show the results when **all** contained tags have the string
    - `'excludeAND'`
      - For tags: only shows results that **don't** contain **all** the passed tags
      - For string: only show the results when **all** the contained tags **don't** contain the string
    - `'includeOR'`
      - For tags: only show results that contain **at least one** of the passed tags
      - for string: only show results when **at least one** of the tags contain the string
    - `'excludeOR'`
      - For tags: only show results that **don't** contain **at least one** of the passed tags
      - For string: only show results when **at least one** of the tags **don't** contain the string
  - `where` (optional) - A `Object` that defines where the search will be made, this objett contains:
    - `actor` (optional) - A `boolean` that defines what actors will be searche, this object contains:
      - `global` (optional) - A `boolean` that defines if actors from the actor directory should be searched for tags
      - `scene` (optional) - A `boolean` that defines if actors from the current scene should be searched for tags
      - `player` (optional) - A `boolean` that defines if the players should be searched for tags
    - `item` (optional) - A `Object` that defines what items will be searched, this object contains:
      - `global` (optional) - A `boolean` that defines if items inside the item directory should be searched for tags
      - `actor` (optional) - A `boolean` that defines if items inside the actors from the actor directory should be searched for tags
      - `scene` (optional) - A `boolean` that defines if items inside the actors from the current scene should be searched for tags
      - `player` (optional) - A `boolea` that defines if items inside the players should be searched for tags
  - `tags` (optional) - A `string array` containing the tags that will be used for filtering (take a look at the tips below, before [`SearchActor()`](#search-actor))
  - `string` (optional) - A `string` containing the string that will be used for filtering (take a look at tips below, before [`SearchActor()`](#search-actor))

This method returns a `Object` like this:
```js
{
    // If a category has no results, it will be undefined, i.e:
    // no global actors got found, so actors.global will be undefined
    // If all the values from a type are undefined, it will be undefined too, i.e:
    // actors.global, actors.scene and actors.player are undefined, so actors will be undefined
    // If actors and items are undefined, them the returning value of the method will be undefined too
    actors: { // The actors that got found
        global: [] // From the actor directory
        scene: [] // From the current scene
        player: [] // From the players
    }
    items: { // The items that got found
        global: [] // From the item directory
        actor: [] // From the actor directory
        scene: [] // From the current scene
        player: [] // From the players
    }
}
```

Lets say you want to get all the items and actors that have at least one tag set:
```js
ItemTags.SearchAll();
```
Thats it, simple as that.

Now one that is a little bit more complex, imagine you want to find all the items on your world that are **not** made of metal, for this scenario consider that you have tagged the metallic items as `metal`:
```js
ItemTags.SearchAll({
    tags: ['metal'],
    method: 'excludeOR', // You could use 'excludeAND' too if you have only one tag to search
    where: {
        actor: false, // We just want items
        item: true, // We want to find ALL the items
    }
})
```

The returned Object will contain only items that **don't** have the metal tag set.

Lets imagine a more realistic use, lets say we have a spell that makes all magical wooden items in a area turn into dust and vanish, you could get all the wooden items like this:
```js
ItemTags.SearchAll({
    tags: ['wood', 'magic'], // We want magical wooden items to be affects, not only wood, not only magic
    method: 'includeAND', // Since we want the items with BOTH tags set, we need to use includeAND
    where: {
        actor: false, // We are not searching for actors, just items
        item: {
            global: false, // We don't need it
            actor: false, // We don't need it
            scene: true, // The only opton we need, items that are inside a actor from the current scene
            player: false, // We don't need it
        }
    }
})
```
The returned Object will contain only the items that have **both** the `wood` and `magic` tags set.

If you are trying to do something and these examples are not enough, feel free to join my [Discord](https://discord.gg/RAgPXB4zG7) and ping me `@zotydev` and I will help you!

> Yes, the returned values may be duplicated, i.e your actor being contained in `player` and `scene`. I've tried many designs and this is the best one I found since its simple and easy to use. ~~If someone really needs this, I will try another approach, but for now I'm not considering it~~

> The `method` option will default to `'includeAND'`.

> All the options inside `where` are optional, if you don't pass any of the values it will default to `true`. You can set any of the values (including `where` itself, `where.item` and `where.actor`) to `false` to exclude them from the search.

> There are two optional values, `tags` and `strings`, only one will be used for the search, if you include both, the `tags` option will be used. And if you don't pass both the search will return all the results that have atleast one tag set.

### Search Actor
```js
ItemTags.SearchAtor(actor, options);
```
- `options` - A `Object` that defines the options for the search
  - `method` (optional) - A `string` that defines what filtering method will be used when `tags` or `string` is passed, this value can be:
    - `'includeAND'`
      - For tags: only shows results that contain **all** the passed tags
      - For string: only show the results when **all** contained tags have the string
    - `'excludeAND'`
      - For tags: only shows results that **don't** contain **all** the passed tags
      - For string: only show the results when **all** the contained tags **don't** contain the string
    - `'includeOR'`
      - For tags: only show results that contain **at least one** of the passed tags
      - for string: only show results when **at least one** of the tags contain the string
    - `'excludeOR'`
      - For tags: only show results that **don't** contain **at least one** of the passed tags
      - For string: only show results when **at least one** of the tags **don't** contain the string
  - `tags` (optional) - A `string array` containing the tags that will be used for filtering (take a look at the tips below, before [`SearchActor()`](#search-actor))
  - `string` (optional) - A `string` containing the string that will be used for filtering (take a look at tips below, before [`SearchActor()`](#search-actor))

This method returns a `Object array` containing the items that got found, if no items match the filters it returns `undefined`.

Usage example: lets say you taged all the items on your world, and the items that emit light all have the `light_` prefix, you can easily find the light emitting items of a certain actor like this:
```js
let actor = ... // Where you are getting your actor Object from
ItemTags.SearchActor(actor, {
    string: 'light_', // This is the string that defines
    method: 'includeOR', // As stated before, this defines that atleast one tag should contain the passed string
})
```
This way we will search all the items of a actor and only the ones that have atleast one tag with the `light_` string inside of it will be returned.

> PS: Don't do this :P Its just a example and is not a good idea to replicate, if you want to do something similar try using combination of tags, like `light` and `emit`. This way you can benefit from the individual tags if you need _idk if someone will ever get to this level of complexity, but its possible :D_
