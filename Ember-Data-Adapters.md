Adapters take requests from the store and converts them into actions for your server. They can be model-specific or application-wide.

Adapters have 7 methods to override:

* `find(store, type, id, snapshot)` - `GET` request to the URL returned by `buildURL`
* `createRecord(store, type, snapshot)` - Called by `save()`. Serializes, then `POST`s to `buildURL`
* `updateRecord(store, type, snapshot)` - Serializes, then `PUT`s to `buildURL`.
* `deleteRecord(store, type, snapshot)` - `DELETE`s to `buildURL`
* `findAll()` - Private in the REST adapter, implemented by `find()`
* `findQuery(store, type, query)` - `GET` to `buildURL`, with query serialized as parameters
* `findMany(store, type, ids, snapshots)` - Coalesces multiple find requests to one `GET` request

## REST Adapter Methods

* `buildURL(modelName, id, snapshot, requestType, query)` - builds a URL for a request. Uses `urlFor<requestType>()` internally, which in turn uses `_buildURL()`. Builds from `host` & `namespace` properties of adapter, and the `model`, and `id` properties of the request.
* `ajaxSuccess()` / `ajaxError()` - Do something with response metadata
* `findHasMany` / `findBelongsTo` - Make a `GET` request to a set of unloaded records from links

## Adapter Properties

* `namespace: "api/1"` - prepended to all calls
* `host: "http://example.com"` - override if different URL than app
* `defaultSerializer: "serializerName"` - override if serializer name different than adapter name
* `headers: {}` - hash of headers to send with every request, can be volatile

## Serializers

Format the server call and response. Have 3 main methods:

* `extract()` -  Deserializes response from server
* `serialize(snapshot, options)` - Converts your record to the form your server wants. Options has one boolean property: `includeId`.
* `normalize(typeClass, hash, prop)` - Formats server response into what `store.push()` wants. Transform the hash, send the normalized payload to _super().

## RESTSerializer Methods

* `extractSingle(store, typeClass, payload, id)` - Called when the response is returning a single record. Restructure payload- leave more fine-grained conversion for `normalize()`. Call `this._super(<signature>)` to finish the method.
* `extractArray(store, primaryTypeClass, payload)` - Called when the response has multiple records.  Otherwise the same as extractSingle.
* `payloadKeyFromModelName(modelName)` / `modelNameFromPayloadKey(key)` - If model name is different in ember than it is on the server.
* `serializeIntoHash(hash, typeClass, snapshot, options)` - customize root keys of the JSON
* `serializePolymorphicType(snapshot, json, relationship)` - Defines how polymorphic types are represented in JSON

## RESTSerializer Properties

* `normalizeHash` - Takes a hash of functions to transform specific properties
* `Pluralize` - camelCase attributes

Use transforms for strings, numbers, dates.

## Snapshots

```
post.get('id')           => postSnapshot.id
post.get('title')        => postSnapshot.attr('title')
post.get('author')       => postSnapshot.belongsTo('author')
post.get('comments')     => postSnapshot.hasMany('comments')
post.constructor         => postSnapshot.type;
post.constructor.typeKey => postSnapshot.typeKey
```

Underlying record is in snapshot.record

## Notes

* Don’t switch APIs, switch adapters
* Use HTTP Mocks instead of fixtures
* Model shouldn’t care how it’s represented on the server
* Don’t pollute models with serializer concerns
* Refer to serialize in `normalize()`

### History

* Model hook used to use $.get()
* Then it had to map underscore to camelCase
* And then it...

### Compound keys

* Handled in “normalize” method
* Define keys in serializer
* `typeClass` is the class for a given model
