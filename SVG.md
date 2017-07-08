## Notes

* Written in XML
* Wrapped around an <svg> element, which has width/height attributes.
* `<g>` = group
* `<image x=# y=# width=# height=# xlink:href=url>`
* `<use x=# y=# width=# height=# xlink:href=id>`

## Shapes

* `<rect>`
* `<circle>`
* `<ellipse>`
* `<line>`
* `<polyline>`
* `<polygon>`
* `<path>`
* `<text>`

## Strokes

* `stroke`
* `stroke-width`
* `stroke-linecap` (`butt`, `round`, `square`)
* `stroke-dasharray` (custom dashes)

## Filter Definitions

```svg
<defs>
    <filter id=id x=# y=#>
        //Filter here
    </filter>
    <linearGradient id=id x1=# y1=# x2=# y2=#>
        <stop offset=# stop-color=color stop-opacity=# />
    <linearGradient>
    <radialGradient id=id cx=# cy=# r=# fx=# fy=#>
        <stop offset=# stop-color=color stop-opacity=# />
    </radialGradient>
</defs>
```

## Filters

* `<feBlend>`
* `<feColorMatrix>`
* `<feComponentTransfer>`
* `<feComposite>`
* `<feConvolveMatrix>`
* `<feDiffuseLighting>`
* `<feDisplacementMap>`
* `<feFlood>`
* `<feFuncA>`
* `<feFuncB>`
* `<feFuncG>`
* `<feFuncR>`
* `<feGaussianBlur>`
* `<feImage>`
* `<feMerge>`
* `<feMergeNode>`
* `<feMorphology>`
* `<feOffset>`
* `<feSpecularLighting>`
* `<feTile>`
* `<feTurbulence>`
