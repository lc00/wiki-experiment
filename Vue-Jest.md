* Testing library is `@vue/test-utils`
* Mount comonents with `shallowMount` and `mount`

```
shallowMount(component, {
  propsData: {},
  data: {},
})
```

## Arrange methods

* `.find(selector)`
* `.findAll(selector)`
* `.setData()`, `.setProps()`
* `.props()`

## Act methods

* `.trigger(event)`
* `.setValue()` / `setChecked()` / `setSelected()`

## Assert methods

* `.text()`
* `.exists()`
* `.emitted(event)`
* `.contains(selector)`
* `.isVisible()`
* `.classes()`
* `.attributes.()`

Escape hatches:

* `.vm` - Access to the component object
* `.element` - Access to the underlying DOM element
* `.html` - Access to the underlying HTML element

```js
import { shallowMount } from "@vue/test-utils";
import HelloWorld from "@/components/HelloWorld.vue";

describe("Emitting", () => {
  it("emits", () => {
    const component = shallowMount(HelloWorld);
    component.find("button").trigger("click");
    expect(component.emitted().pizza).toBeTruthy();
  });
});
```
