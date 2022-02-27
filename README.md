# AtomSettings

These are the packages and settings/snippets I use in Atom (to be extended).

Even though the solution with `latex`+`pdf-view` worked nicely for me, it nevertheless lacked functionality and, most importantly, I couldn't find a way to get clickable hyperrefs. That's why I switched from `pdf-view` to `pdfjs-viewer` which, unfortunately, isn't yet supported by `latex` and seemed to be lacking SynchTeX support at first.
By changing `pdf-view` to `pdfjs-viewer` in
```
~/.atom/packages/latex/lib/openers/pdf-view-opener.js
```
and uncommenting
```
this.element.contentWindow.addEventListener('contextmenu',
   (event) => this.handleSynctex(event))
```
in
```
~/.atom/packages/pdfjs-viewer/lib/pdfjs-viewer-view.js
```
I could work around these issues, though.
