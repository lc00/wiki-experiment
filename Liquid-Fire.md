## Template Helpers

* `{{liquid-outlet}}` - Route transitions
* `{{liquid-with}}` - Transition between models or contexts in a single route
* `{{liquid-bind}}` - Updates to bound values
* `{{liquid-if}}` - Changes to true/false values
* `{{liquid-spacer}}` - Smoothly growing and shrinking container

These don’t automatically update when bound data changes, they check the transition map to see if any transitions match first.

## Transition Map

Declares transitions, each of which can have a set of constraints. The first transition that matches all constraints executes the `use` function. `setDefault` allows you to enable global animation settings, like easing.

## Transitions

Each transition has one `use()` statement. It can have one `reverse()` statement, which is used if the `fromRoute`/`fromModel` and `toRoute`/`toModel` are reversed. Can send a callable or a function.

## Constraints

Each of these accepts a string, list of strings, expression, or combinations of these.

* `fromRoute()`
* `toRoute()`
* `withinRoute()`

Each of these accepts `{instanceOf: modelName}`:

* `fromModel()`
* `toModel(function(fromModel, toModel){})`
* `betweenModels()`
* `betweenNonEmptyModels()`

Can also be based on DOM state:

* `hasClass()`
* `childOf()`

## Predefined Transitions

* `toLeft`
* `toRight`
* `toUp`
* `toDown`
* `crossFade`
* `fade`

## Custom Transitions

`insertNewView is a promise that resolves to `newView`. Allows you to animate the views in parallel or in series.

```
function(oldView, insertNewView, options){
    stop(oldView);
    return animate(oldView, {
        opacity: 0
    })
}).then(insertNewView)
.then(function(newView){
    return animate(newView, {
        opacity: [0, 1]
    });
});
```

## Animation Primatives

* `animate(view, properties, options, label)`. Returns promise.
* `stop(view)`
* `finish(view, label)`. Returns a promise that resolves when animation is complete.
* `isAnimating(view, label)`
* `timeSpent(view, label)`
* `timeRemaining(view label)`

## Modals

Uses own syntax for creating animated modals.
