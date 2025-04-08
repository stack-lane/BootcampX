# HTML

- There are a total of 100 HTML tags.

Here's a list of some common and important HTML tags:

| #   | Category                 | Description                                       | Example Tags                                              |
| --- | ------------------------ | ------------------------------------------------- | --------------------------------------------------------- |
| 1   | Document Metadata        | Defines metadata and instructions for the browser | `<html>`, `<head>`, `<title>`, `<meta>`, `<link>`         |
| 2   | Sectioning Content       | Organizes content into logical sections           | `<header>`, `<nav>`, `<section>`, `<article>`, `<footer>` |
| 3   | Text Content             | Displays text and related formatting              | `<h1>`–`<h6>`, `<p>`, `<span>`, `<strong>`, `<em>`        |
| 4   | Lists                    | Defines ordered, unordered, or descriptive lists  | `<ul>`, `<ol>`, `<li>`, `<dl>`, `<dt>`, `<dd>`            |
| 5   | Hypertext & Links        | Creates links to other pages or resources         | `<a>`, `<link>`                                           |
| 6   | Media                    | Embeds visual or audio media                      | `<img>`, `<audio>`, `<video>`, `<source>`, `<track>`      |
| 7   | Forms & Input            | Captures user input and submits data              | `<form>`, `<input>`, `<textarea>`, `<select>`, `<button>` |
| 8   | Tables                   | Displays tabular data                             | `<table>`, `<tr>`, `<td>`, `<th>`, `<thead>`, `<tbody>`   |
| 9   | Scripting & Programmatic | Adds scripts or defines programmatic behaviors    | `<script>`, `<noscript>`, `<template>`, `<canvas>`        |
| 10  | Embedded Content         | Embeds other documents or applications            | `<iframe>`, `<embed>`, `<object>`                         |

# Basic Structure Of HTML Document

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Web Page</title>
  </head>
  <body>
    <h1>Hello, world!</h1>
    <p>This is a basic HTML document.</p>
  </body>
</html>
```

- `<!DOCTYPE html>` specifies the type of document this is -- in this case, a HTML document.
- `<html>` is the root element. Semantically, there should only be one root `<html>` element per HTML file/document. Although the syntax of HTML is very forgiving in that sense.
- `<head>` contains meta-information about the document (not visible on the page, although can be used by the browser to render some of this onto tab titles and all).
- `<body>` contains all the visible elements of the page such as headings, paragraphs, links, etc.

## Elements/Tags

- [Void elements](https://developer.mozilla.org/en-US/docs/Glossary/Void_element)
- [Attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes) & [Booealn Attributes](https://developer.mozilla.org/en-US/docs/Glossary/Boolean/HTML)
- [Character References](https://developer.mozilla.org/en-US/docs/Glossary/Character_reference)

## Browser

- The browser takes in HTML and CSS and produces a DOM (Document Object Model) and a CSSOM (CSS Object Model) from them, respectively.
- The DOM is an in-memory representation of the HTML (think of it as a tree structure written in C++), while the CSSOM is an in-memory representation of the CSS (like a tree or list structure, also implemented in C++).
- The browser then combines the DOM and CSSOM to form a Render Tree, which is a hierarchical tree-like structure representing only the visible elements on the page, along with their computed styles.
- The browser uses this Render Tree to calculate the final positions and sizes of elements based on the viewport size, font metrics, layout rules, and more. This step is called the Layout Pass (also known as Reflow).
- Once layout is done, the browser paints actual pixels for each visible element — this is called the Paint phase.
- These painted layers are then composited (often with GPU acceleration) to produce a final frame, which is then rasterized and displayed on the screen.

## Web Server

- You → open example.com
- Browser → sends a request to a web server
- Web Server → sends back the HTML, CSS, JS, etc.
- Browser → parses, renders, paints... boom! Page appears

---

**Reference** <br/> [MDN's HTML Tutorial](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started)
