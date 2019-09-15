## Examples

* `expect(result).to.equal("some string")`
* `expect(result).to.not.equal("some string")`
* `expect(result).to.be.true`
* `expect(result).to.be.a("string")`
* `expect(result).to.be.empty`
* `expect(result).to.have.property("key", "value")`
* `expect(result).to.have.nested.property("key.nestedKey", "value")`
* `expect(result).to.have.ordered.members([1, 2, 3])`
* `expect(result).to.include(1)`
* `expect(result).to.include("some sub string")`
* `expect(result).to.match(/regex/)`
* `expect(result).to.have.lengthOf(3)`

## Chainers

No effect, just helps readability

* `to`
    * `be` / `have` / `have.been`
    * `still` / `still.be` / `still.have`
* `has`
* `is`
    * `same`
    * `still`
* `does`
* `and` / `but` / `with`
* `of` / `at` / `that` / `which`
* `a` / `an`

## Equality

* `deep` / `eql` / `eqls` - Uses deep equality for `equal`, `include`, `members`, `keys`, and `property`
* `equal` / `eq` / `equals` - `===`
* `satisfy(matchingFunction)` - Custom matching function
* `a('type')`
* `not` - Negates all following assertions
* `true`
* `false`

## Types

* `null`
* `undefined`
* `NaN`
* `exist`
* `ok`

## Arrays

* `empty`
* `lengthOf`
* `members('keyOne', 'keyTwo')` / `member('key')`
* `keys('keyOne', 'keyTwo')` / `key('key')`
* `ordered` - Enforces an order on `members` assertions
* `include('someMember')`

## Objects

* `empty`
* `property(key)`,  `property(key, value)`
* `keys('keyOne', 'keyTwo')` / `key`
* `include({someKey: someMatchingValue})`
* `instanceOf`
* `any` - At least one key from a `keys` assertion
* `all` - Every key from a `keys` assertion
* `nested` - Enables dot and bracket for `property` and `include` assertions
* `own` - Ignores inherited properties for `property` and `include`
* `respondTo` / `respondsTo` - Has a particular method

## Strings

* `empty`
* `string(stringToMatch)`
* `include('some sub string)`
* `lengthOf`
* `match`

## Rare

* `oneOf("option1", "option2")`
* `extensible`
* `sealed`
* `frozen`
* `itself` - Owns a property rather than having it in the prototype chain
* `ownPropertyDescriptor`
* `arguments` - Is an arguments object
* `expect(target()).change(result())`
* `throw() / `throws()`` - Asserts that an error constructor or message was thrown
* `fail`

### Numbers / Dates

Rely on precise values instead of these

* `least`
* `most`
* `above`
* `below`
* `increase`
* `decrease`
* `closeTo(target, delta)`
* `by`
* `within`
* `finite`

## Notes

* Use a type-check with `includes`, `empty`, `keys`
