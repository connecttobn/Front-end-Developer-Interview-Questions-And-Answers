# HTML Questions

#### What does a `doctype` do?

It specifies which markup standard the page is using. With the information, the
browser determines how to render the page according to the page's source code.

#### What's the difference between standards mode and quirks mode?

They are modes used by browser rendering engines. In the standards mode, the
engine will render a page as HTML and CSS specifications specify. The quirks
mode is to render legacy pages written before these standards are fixed. The
legacy pages contain non-standard behaviours emulated in old browsers such as
Internet Explorer 5 or Navigator 4.

We can enforce browsers to use standards mode with a `<!DOCTYPE html>` tag.

#### What's the difference between HTML and XHTML?

XHTML falls under family of XML markup languages. 
In other words, before HTML5, XHTML defined strict rules for HTML.
XHTML can be properly parsed using strict parsers, meaning every tag would be properly closed.
On the other hand, HTML doesn't strictly follow this. And hence it needs lenient parser.
XHTML standard was developed by w3c. Similarly XHTML5 is on its way for HTML5.

#### Are there any problems with serving pages as `application/xhtml+xml`?

IE < 8 will show a download dialog for the pages, instead of rendering them
properly.

#### How do you serve a page with content in multiple languages?

Use `lang` (or `xml:lang` for XHTML) in tags. Also metadata and
`Content-Language` HTTP header can be used.

#### What kind of things must you be wary of when design or developing for multilingual sites?

- `hreflang` attr in link
- `dir` attr indicating language direction, such as `rtl`
- `<meta charset='UTF-8'>`
- `font-size` for `:lang({language_code})` selectors in CSS
- difference in word length for each language

#### What are `data-` attributes good for?

It makes HTML elements contain extra information without using non-standard
attributes, or other hacks like that.

#### Consider HTML5 as an open web platform. What are the building blocks of HTML5?

- *Semantic Elements* like `<header>`, `<footer>`, `<article>`, and `<section>`
- Form Element attributes: number, max, min, pattern, date, time, calendar, and range.
- New APIs like: 
    - Geolocation `navigator.geolocation`
    - Drag and Drop
    - Web Storage : `localStorage` , `sessionStorage`
    - Web Workers : EventSource
    - SSE Server Side Events
 
#### Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.

- `cookie` Cookies are primarily for reading server-side, local storage can only be read by the client-side.
Max size allowed is 4095 Bytes(~4kb) per cookie

- The `sessionStorage` property allows you to access a session Storage object for the current origin. `sessionStorage` gets cleared when the page session ends. A page session lasts for as long as the browser is open and survives over page reloads and restores. Max size allowed is 5MB

-`localStorage` property allows you to access a Storage object for the Document's origin; the stored data is saved across browser sessions. localStorage is similar to `sessionStorage`, except that while data stored in localStorage has no expiration time. Max size allowed is 5MB

#### Describe the difference between `<script>`, `<script async>` and `<script defer>`.

- `<script>` stops rendering process, and download and run a script.
- `<script async>` don't stop rendering process while asynchronously
  downloading a script. When finishing download, it stops rendering and runs the
  script.
- `<script defer>` don't stop rendering process while asynchronously
  downloading a script. When finishing rendering, it runs the script.

#### Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?

moving stylesheets to the document HEAD makes pages appear to be loading faster. This is because putting stylesheets in the HEAD allows the page to render progressively.
Generally library script such as the jQuery are put in the head section. So any script which is needed before the body is rendered should be kept in head.

JS Scripts can be placed anywhere in the document, in head or body or footer. 
The problem with writing scripts at the head of a page is blocking. The browser must stop processing the page until the script is download, parsed and executed If you think its heavy, its better to load at the end so page loads progressively. 

#### What is progressive rendering?

The techniques used to render content for display as quickly as possible is called as progressive rendering..
Lazy loading : example depending upon viewport,images could be loaded with JS.
Instead of loading the whole data, bring to client on demand or what can be visible

Other way is to prioritising the content in the page. making sure that bare minimum text and CSS, JS is loaded before full media rich content is loaded.

#### Have you used different HTML templating languages before?

Jinja2 and Django templates language in Python. Jade and EJS in JavaScript.

The `<template>` tag holds its content hidden from the client.
Content inside a `<template>` tag will not be rendered.
The content can be visible and rendered later by using JavaScript.
