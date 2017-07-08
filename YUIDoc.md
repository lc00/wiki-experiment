## Notes

* Install globally with `npm -g yuidocjs`
* Run with `yuidoc .`
* Save options with yuidoc.json including project description, etc.
* Every source tree must have one module, every module must have at least one class

```js
/**
* Overall description
* 
* [@type-of-thing] [thingName]
* [@part-of-thing] {[part-type]} [part-name] Description of part
**/
```

## Blocks

* Primary blocks- every comment block is one of these:
    * `module - [name]` - group of related classes
    * `main - [name]` - after module to indicate it is the primary module
    * `class [name]` - should be be above all things it owns, followed by constructor or static
    * `method [name]` - goes right above method, followed by params and return
    * `event [name]` - has params that hang off the event
    * `property [type]` - after each property in a class
* Secondary blocks- these are used in a primary block:
    * `param {[type]} [[optionalName]]|[name] [description]` - Can nest with dot.syntax.
    * `return {[type]} [description]` - return value
    * `async` - Method is asynchronous and requires a callback
    * `chainable` - returns this, so can be chained
    * `example [code-example]` - Syntax-highlighted usage example


## OOP

* `constructor` | `static` - Can instantiate or not
* `namespace [name]` - Allows you to use simple class names without modules
* `extends` | `uses [class-name]` - Links back to parent documentation. Multiple uses.
* `final` | `readOnly` | `writeOnce` - Whether it should be modified
* `throws {[type]} [description]` - indicates the kind of error a method throws
* `private` | `protected` - private won’t have documentation generated

## Properties

* `type [type]` - Indicate type for a property
* `default` - After a type to indicate a property’s default.

## Availability

* `deprecated [Instructions]` - Will be removed
* `since [version]` - Indicates that it was added in this version
* `beta` - might break compatibility in the future

## Examples

### Class

```js
/**
* This is the description for my class.
*
* @class MyClass
* @constructor
*/
```

### Method

```js
/**
* My method description.  Like other pieces of your comment blocks, 
* this can span multiple lines.
*
* @method methodName
* @param {String} foo Argument 1
* @param {Object} config A config object
* @param {String} config.name The name on the config object
* @param {Function} config.callback A callback function on the config object
* @param {Boolean} [extra=false] Do extra, optional work
* @return {Boolean} Returns true on success
*/
```

### Property

```js
/**
* My property description.  Like other pieces of your comment blocks, 
* this can span multiple lines.
* 
* @property propertyName
* @type {Object}
* @default "foo"
*/
```
