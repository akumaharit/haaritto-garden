---
{"dg-publish":true,"permalink":"/2-areas/programming/web/w3-school-bootstrap5/","tags":["w3school"],"created":"2025-10-05T22:15:42.399+07:00","updated":"2025-10-11T21:59:32.862+07:00"}
---

Difference between bootstrap5 and 3/4 is that 5 is now using JavaScript instead of JQuery, but IE11 and down is not supported anymore.
### Getting Started
You could just import bootstrap 5 in the website by using these code in the `<head>` section.
This way is called CDN (Content Delivery Network), so you don't have to download and host BootStrap5 for yourself.
Main advantage: is many user may have downloaded it from jsDelivr when visiting another site, so when visiting this one it will be faster as it is loaded from cache.
```html
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
```
### Containers
- Containers, there are two types of containers `.container` which will expand in a different breakpoints and `.container-fluid` which will always span the entire width of the screen. 
- By default, containers have left and right paddings, no top and bottom padding. We use spacing utilities to make them look better such as `.pt-5` means adding large top padding. 
- You can specify border using `border`. The bg-color using `bg-dark` , `bg-primary` The text color using `text-white`
- You can use `.container-sm|md|lg|xl` to determine **when the container should be responsive.** The higher, it will be responsive for the bigger viewport. (eg. `-container-xxl` will stop being responsive after >=1200px but `-container-sm` will be responsive until 576 px)
### Grid System
It is built with flexbox up to **12 columns across the page**. You can group if you don't want to use 12 columns. You can create unequal columns, but it need to sum up to 12 columns. The pattern of the class is : `col-*-*` the first one represents responsiveness while second one represents a number (like a partition by 12). if the second one is not specify, bootstrap will handle the layout automatically. The grid responsiveness has six classes `.col-` or `.col-|sm|md|lg|xl|xxl|-`
```html
<!-- Control the column width, and how they should appear on different devices -->
<div class="row">
  <div class="col-*-*"></div> 
  <div class="col-*-*"></div>
</div>
<div class="row">
  <div class="col-*-*"></div>
  <div class="col-*-*"></div>
  <div class="col-*-*"></div>
</div>

<!-- Or let Bootstrap automatically handle the layout -->
<div class="row">
  <div class="col"></div>
  <div class="col"></div>
  <div class="col"></div>
</div>
```
If you specify responsiveness for all the columns, they will automatically stack on top of each other when threshold is reached. However, if you didn't specify anything such as left being `col`, it will start to stack each other one by one. (the right side will go to the bottom first)
![Bootstrap5.png](/img/user/3%20Resources/Attachment/Bootstrap5.png)
```html
<div class="row">
  <div class="col-lg bg-dark border text-white">col-lg Number1</div>
  <div class="col-sm bg-dark border text-white">col-sm Number2</div>
  <div class="col-sm bg-dark border text-white">col-sm Number3</div>
  <div class="col-sm bg-dark border text-white">col-sm Number4</div>
  <div class="col-sm bg-dark border text-white">col-sm Number5</div>
</div>
```

### [Typography](https://www.w3schools.com/bootstrap5/bootstrap_typography.php)
![Font size and rem.png|400](/img/user/3%20Resources/Attachment/Font%20size%20and%20rem.png) [ref](https://www.google.com/url?sa=i&url=https%3A%2F%2Fopenclassrooms.com%2Fen%2Fcourses%2F5265446-build-your-first-web-pages-with-html-and-css%2F5282851-control-font-sizes-line-spacing-and-word-spacing&psig=AOvVaw1HdA3B6nsDz0vkib4VUSbA&ust=1760278342572000&source=images&cd=vfe&opi=89978449&ved=0CBUQjRxqFwoTCLjc0PypnJADFQAAAAAdAAAAABAp)
Bootstrap 5 uses a default `font-size` of 1rem (16px by default), and its `line-height` is 1.5.
In addition, all `<p>` elements have `margin-top: 0` and `margin-bottom: 1rem` (16px by default).
- You can add `.h1` to `.h6` to make them behave as heading if you want.
- `.display-1` to `.display-6` to make them stand out more than normal heading
- Bootstrap 5 will style `<mark>` and `.mark` with a yellow background color and some padding
- Bootstrap 5 will style the HTML `<abbr>` element with a dotted border bottom and a cursor with question mark on hover
- Add the `.blockquote` class to a `<blockquote>` when quoting blocks of content from another source. And when naming a source, like "from WWF's website", use the `.blockquote-footer` class:
- `<dl>` for description list. `<dt>` and `<dd>` 
- `<code>` for the code block just like in this page.
- `<kbd>` for keybord input
- `<pre>` for multiple code lines, as it displayed in fixed-width font, it preserves both spaces and line breaks too.

### Text Colors
The classes for text colors are: `.text-muted`, `.text-primary`, `.text-success`, `.text-info`, `.text-warning`, `.text-danger`, `.text-secondary`, `.text-white`, `.text-dark`, `.text-body` (default body color/often black) and `.text-light` You can also add 50% opacity for black or white text with the `.text-black-50` or `.text-white-50` classes:
{ #c1a0ff}


The classes for background colors are: `.bg-primary`, `.bg-success`, `.bg-info`, `.bg-warning`, `.bg-danger`, `.bg-secondary`, `.bg-dark` and `.bg-light`.
You can combine them to `.text-bg-color` such as `.text-bg-success` to make the bootstrap automatically handle text color for each background color.



### Table
Please refer to [[2 Areas/Programming/Web/CS50Web - HTML and CSS#^3c310a\|CS50Web]] on how to add the table. 
- `.table` to add table (this is the main class and should not be modified, when adding `table-striped` add it as another class in the element.)
- `.table-striped` for zebra striped table
- `.table-bordered` for border on all sides and cell
- `.table-hover` add hover effect on table row.
- `.table-dark` add dark background to the table.
- `.table-borderless` to remove borders from the table.
- You can add contextual classes to `<table> <tr> <td>` (such as `.table-primary`, it is the same one as [[#^c1a0ff|Classes for text colors]])
- Add `.table-responsive` to add a scrollbar to the table when needed (when it is too big horizontally, you can also use `.table-responsive-sm` to `.table-responsive-xxl` to define when the table should get a scrollbar depending on the screen width.

### Images
- `rounded` to add rounded corners to an images.
- `.rounded-circle` shapes the image to a circle.
- `img-thumbnail` shape the images to a thumbnail (bordered)
- align the image when `.float-start` or `.float-end` 
- **Center an image using** `.mx-auto` (`margin: auto;`) and `.d-block` (`display: block;`)
	- the `display: block;` will convert an image that is an in-line element which cannot be center using `margin: auto;` into an block element which can be centered. 
- responsive an image using `.img-fluid` which automatically applied CSS `max-width: 100%;` and `height: auto;` to the image.

### Alerts
- Use div with `.alert` to add alert, which can be followed with one of the contextual class such as `.alert.alert-info`
- To add link inside alert, use `alert-link` in the `<a>` element to create matching colored links.
- Use `.alert-dismissible` for the closing alerts, also add button with `.btn-close` and `data-bs-dismiss="alert"` to make it close the alert box when clicked. Add `.fade` and `.show` to add fading effect when closing the alert message.

### Button
- Use `btn` for the button. It can be used on `<a>` `<button>` and `<input>` elements.
- You can add contextual class such as `.btn.btn-primary` to make it style accordingly.
- Add outline to make it bordered/outline button. `btn-outline-primary`
- Add `btn-lg` or `btn-sm` for large or small button.
- To make block level button, add div with `.d-grid.gap-3` on the parent element.
	- `.d-grid` to arrange item in grid row/columns (CSS Grid Container)
	- `gap-3` **to add space between grid items.**
- For active button use `.active` and disabled simply add attribute `disabled` -> `<button type="button" class="btn btn-primary" disabled>Disabled Primary</button>`
	- For `<a>` add class `.disbled` because `<a>` element cannot be disabled.
- You can also add spinner to a button.