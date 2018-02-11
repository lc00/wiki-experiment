Component library.

## Apps

Declare an HTML selector to control the tree of.

```js
const app = new Vue({
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
    }
});
```

Use it like this:

```html
<h1 v-if="visible" v-bind:title="hover">{{header}}</h1>
<button v-on:click="hideHeader">Hide header</button>
```

## Components

Need to be declared before your app. Make a component like this:

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

```js
Vue.component("todo-item", {
    props: ["message"],
    template: "<p>{{message.text}}</p>"
});
Vue.component("announcement-container", {
    props: ["announcement"],
    template: "<p>{{announcement.text}}</p>"
});

const app = new Vue({
    el: "header",
    data: {
        header: "This is a header",
        hover: "This is hovering",
        visible: true,
        list: [{
            message: "One"
        },{
            message: "Two"
        }],
        messages: [{
            id: 1,
            text: "Hi!"
        },{
            id: 2,
            text: "Oi!"
        }],
        announcement: {
            text: "Announcement!"
        }
    },
    methods: {
        hideSubheader(){
            this.visible = false;
        }
    }
});
```
