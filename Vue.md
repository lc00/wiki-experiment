Component library.

## Instances

* Declare an HTML selector to control the tree of

```js
const vm = new Vue({
    el: "body",
    data: {
        headerText: "This is a header",
        hover: "This is hover text",
        visible: true
    },
    methods: {
        hideHeader(){
            this.visible = false;
        }
    },
    computed: {
        reversedHeader(){
            return this.headerText.split("").reverse("");
        }
    },
    components: {
    }
});
```

Use it like this:

```html
<h1 v-if="visible" v-bind:title="hover">{{header}}</h1>
<button v-on:click="hideHeader">Hide header</button>
<input placeholder="Change the title" v-model="header" />
```

## Components

* Need to be declared before your app
* Are also Vue instances and take the same options object
* Can be declared in a `components` hash in another component
* Data object must be a function
* Uses same data-down/actions-up paradigm as Ember
* Child components can validate types, and requiredness to be passed in
* A property is only reactive if it's declared when constructed
* Working directly with array indexes doesn't trigger reactivity- use `Vue.set()` instead

Make a component like this:

```js
Vue.component("todo-item", {
    props: ["message"],
    template: "<p>{{message.text}}</p>"
});
```

Use it like this:

```html
<todo-item
    v-for="message in messages"
    v-bind:message="message"
    v-bind:key="message.id">
</todo-item>
```

Expecting this to exist in the app:

```js
const app = new Vue({
    el: "main",
    data: {
        messages: [{
            id: 1,
            text: "Hi!"
        },{
            id: 2,
            text: "Oi!"
        }],
    }
});
```

Composing components:

```html
<parent-component>
    <child-component v-bind:child-property="parentProperty"></child-component>
</parent-component>
```

Emitting events:

```js
someMethod(){
    this.$emit("customEvent")
}
```

### Templating

* Simple binding: `<p>{{message}}</p>`
* Toggle classes: `<p v-bind:class="{active:isActive, highlighted:isHighlighted}" class="some-static-class"></p>`
* Outlets: `<slot name="optional-name">Fallback Content</slot>` == `{{outlet}}`
* One-time: `<p v-once>{{message}}</p>`
* Render HTML: `<p v-html="rawHTML"></p>`

You can use expressions in templates, but not statements or control flow:

```html
{{number + 1}}
{{isOk ? "Yes" : "No"}}
{{message.split("").reverse().join("")}}
<p v-bind:class="class + 'string' + 1"></p>
```

Use directives to bind attributes:

```html
<p v-bind:class="class"></p>
<button v-bind:disabled="isDisabled">Button</button>
```

Ways to do two-way binding:

```
<input v-model="message" />
<input type="checkbox" v-model="isChecked" />
<option v-for="item in list" v-bind:value="item.id">{{item.text}}</option>
<input v-model.trim.number.lazy="message" />
```

Toggle multiple classes at once:

```js
computed: {
    someClassObject(){
        return {
            active: this.isActive,
            highlighted: this.isHighlighted
        };
    }
}
```

```html
<p v-bind:class="someClassObject"></p>
```

### Directives

* `v-bind` / `:`
* `v-if`, `v-else-if`, `v-else`
    * Apply to a group of elements with the `<template>` temporary wrapper
* `v-show` - Always rendered, is hidden with CSS when falsy- Better for frequent toggling
* `v-for="item in list"`, `v-for="(item, index) in list"`, `v-for="(value, key, index) in object"`
    * Use `key`s with list items
* `v-on:event="someExpression || someMethod || anotherMethod('hola', $event)"` / `@someEvent`
    * `.stop`, `.prevent`, `.capture`, `.self`, `.once`
    * `v-on:keyup.13`, `v-on:enter|tab|delete|esc|space|up|down|left|right|custom`
    * Can use modifiers

### Computed Properties and Watches

* Watches are the same as observers in Ember, same caveats.
* Computed properties will cache, meaning things like `Date.now()` and `Math.random()` won't trigger recomputes.
* You can `set` and `get` separately if you want

You can watch for a property to change like this:

```js
vm.$watch("someProperty", function(newValue, oldValue){
});
```

or in the `watch` hash:

```js
watch: {
    someProperty(value){
        this.someOtherProperty = value * 2;
    }
}
```

### Lifecycle Hooks

* `created`
* `mounted`
* `updated`
* `destroyed`

![Lifecycle Stages](https://vuejs.org/images/lifecycle.png?_sw-precache=6f2c97f045ba988851b02056c01c8d62)

## Services

```js
const bus = new Vue();

bus.$emit("someEvent", 1);
bus.$on("someEvent", function(id){
    // Something
});
```

## Single File Components

```html
<!-- ComponentName.vue -->
<template>
    <h1>{{message}}</h1>
</template>

<script>
    export default {
        name: "ComponentName",
        props: {
            message: String
        }
    }
</script>

<style lang="scss" scoped>
    $color: blue;
    h1 {
        color: $color;
    }
</style>
```

## Router

```
// router.js
import Vue from "vue"
import Router from "vue-router"
import MyComponent from './views/MyComponent.vue'

Vue.use(Router)

export default new Router({
    routes: [{
        path: "/my-component",
        name: "my-component",
        component: MyComponent
    }]
})
```

## State Management / Vuex

```
const store = new Vuex.Store({
    state: {
        someKey: "someValue",
        someValues: [1, 2, 3]
    },
    mutations: { // Have to be synchronous
        setSomeKey(state, value){
            state.someKey = someValue;
        }
    },
    getters: {
        filterValues(state){
            return state.someValues.filter(value => value < 2);
        }
    },
    actions: { // Don't have to be synchronous
        setSomeKey({commit}){
            commit("setSomeKey");
        }
    }
});

const vm = new Vue({
    el: "body",
    store
});

const component = new Vue.Component({
    methods: {
        doSomething(){
            this.$store.dispatch("setSomeKey");
        }
    },
});

// this.$store.state.someKey
```
