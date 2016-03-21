# Riot Views

This is a collection of reusable riot views. They can be used as components to build up functionality.

Each view is prefixed with `solid-` (Solid Compnonent).

## Guide

### `solid-clamp`

```javascript
require('riot-views/solid-clamp.tag')
```

Dependencies : `clamp-js`

A Clamp can be used to limit the number of lines displayed and ellipsize the last line i fthere is overflow. Internally
it uses a `<yield />`.

Attributes:
* lines: number of lines to clamp to - default: 1

Content:
* Text you want clamped.

```html
<solid-clamp lines="2">
    The following text will be clamped to
    two lines even if the text is longer
    than two lines.
</solid-clamp>
```

### `solid-tabs`

```javascript
require('riot-views/solid-tabs.tag')
```

Dependencies : `velocity`

Tabs with an animated underline.

Attributes:
* tabs: an array of tabs. Each tab item should have a `hash` and a `label` property.
* callback: an optional function that gets called with the active index on each user click.

```javascript
riot.mount(tabsView, {
    tabs : [
        { hash : 'home',        label : 'Home'},
        { hash : 'about',       label : 'About' },
        { hash : 'products',    label : 'Products' }
    ],
    callback : function(index) {
        console.log('new tabs index', index);
    }
});
```

```html
<solid-tabs tabs="{ opts.tabs }" callback="{ opts.callback }"> </solid-tabs>
```

### `solid-raw`

```javascript
require('riot-views/solid-raw.tag')
```

Dependencies : none

Will output html string. Riot by default will not template html. Use this tag when you want to template html.

Attributes:
* content: an html string.

```javascript
riot.mount(rawView, {
    htmlString : '<p>Lorem ipsum dolor sit amet, <strong>consectetur</strong> adipisicing elit, sed do <strong>eiusmod</strong> tempor incididunt ut labore et dolore magna aliqua.</p>'
});
```

```html
<solid-raw content="{ opts.htmlString }"> </solid-raw>
```
