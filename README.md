# AtomSettings

These are the packages and settings/snippets I use in Atom. Their aim is to make writing LaTeX and Python code as convenient as possible.
This is a work-in-progress and many things will change over time, most likely.

As for now, the settings provide a convenient Overleaf-esque environment for writing LaTeX documents (split-screen and SynchTeX):
The default snippets for `language-latex` are disabled and custom snippets for defining environments, etc. are provided in `snippets.cson`, e.g. `fig+TAB` triggers
```
\begin{figure}[h]
  \centering
    \includegraphics[width=\textwidth]{}
      \caption[]{Caption}
      \label{fig:Label}
\end{figure}
```
in a **new** line, i.e. you don't have to press `RETURN` before inserting a figure. Similarly, `m+TAB` lets you write in-line math quickly.
My aim is to optimize the TAB-stops in all those snippets and avoid unnecessary arrow-key presses. As already mentioned: This is a WIP.


Note regarding LaTeX split-screen: Even though the solution with `latex`+`pdf-view` worked nicely for me, it nevertheless lacked functionality and, most importantly, I couldn't find a way to get clickable hyperrefs. That's why I switched from `pdf-view` to `pdfjs-viewer` which, unfortunately, isn't yet supported by `latex` and seemed to be lacking SynchTeX support at first.
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
