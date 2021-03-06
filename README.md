vminpoly
========

A polyfill for CSS units vw, vh &amp; vmin.

Online [demo](http://saabi.github.com/vminpoly) right here.

This is a working proof of concept right now. There's a lot of cleanup to do on the code.

Since most browsers ignore rules they don't understand, the code must load and parse the original CSS sourcecode. It does this uning a javascript [CSS parser](https://github.com/tabatkins/css-parser). Once this is done, it filters the generated tree leaving only rules that use 'vh', 'vw' & 'vmin' units.
At window resize time, it generates CSS code for the 'px' equivalents and appends it in a 'style' element at the end of the 'head' element. The generated code respects media queries.

As it is, it's fast enough for a lot of cases, but the code can still be optimized greatly, both in parsing and in resizing.

Also, any suggestions on how to better organize the repo, specially with respect to third party code, is greatly appreciated.

TODO:
-----

* Add feature detection, at the moment it's doing its stuff even in browsers that support the units.
* IE9 and IE10 support vw, vh & vm, so the code should only translate 'vmin' units to 'vm'
* Only linked stylesheets are being parsed right now but it's very easy to also parse 'style' elements.
* The CSS parser has some trouble parsing some whitespaces it seems. So that has to be looked into...
* tokenizer.js fails in IE8, so no luck there and I presume in earlier IEs for now. It's working fine in IE9, Firefox and Opera, which doesn't support any of the units. Chrome, Safari and the Firefox beta don't need it.
* Well... Chrome and Safari actually can benefit from it as they don't properly handle font-size natively while resizing the window.
* Add some more examples of what can be achieved.

In short, the only browser with apparently full native support right now is Firefox beta (Aurora). The rest will benefit from this polyfill immediately, even without the badly needed code polishing.