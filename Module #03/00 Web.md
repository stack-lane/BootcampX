# Web

HTML, CSS, and JavaScript are the main three technologies you'll use to build a website.

- HTML is for structure and semantics (meaning).
- CSS is for styling and layout.
- JavaScript and APIs are for controlling dynamic behavior.

## Basics

### HTML

HyperText Markup Language, or HTML, is a markup language consisting of different elements you can wrap (mark up) content in to give it meaning (semantics) and structure. Simple HTML looks like this:

```html
<h1>Hello, World</h1>

<p>I'm a piece of code on BootcampX repository.</p>
```

### CSS

Cascading Style Sheets (CSS) is a rule-based language used to apply styles to your HTML — for example, setting text and background colors, adding borders, animating things, or laying out a page in a certain way. As a simple example, the following code would turn all HTML paragraphs red:

```css
p {
  color: red;
}
```

### JavaScript (and APIs)

JavaScript is the programming language we use to add interactivity to websites, from dynamic style switching, to fetching updates from the server, right through to complex 3D graphics. The following simple JavaScript store a reference to a paragraph in memory and change the text inside it:

```javascript
const pElement = document.querySelector("p");
pElement.textContent = "We changed the text!";
```

## Web Best Practices

When doing web development, the main cause of uncertainty comes from the fact that you don't know what combination of technology each user will use to view your website:

- User 1 might be looking at it on an iPhone, with a small, narrow screen.
- User 2 might be looking at it on a Windows laptop with a widescreen monitor attached to it.
- User 3 might be visually impaired, and using a screen reader to read and interact with the web page.
- User 4 might be using a really old desktop machine that can't run modern browsers.

Because you don't know exactly what your users will use, you need to design defensively — make your website as flexible as possible, so that all of the above users can make use of it, even if they might not all get the same experience.
