---
{"dg-publish":true,"permalink":"/0-inbox/bootstrap5/","tags":["w3school"],"created":"2025-10-05T22:15:42.399+07:00","updated":"2025-10-05T22:46:38.323+07:00"}
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
Containers, there are two types of containers `.container` which will expand in a different breakpoints and `.container-fluid` which will always span the entire width of the screen. 
By default, containers have left and right paddings, no top and bottom padding. We use spacing utilities to make them look better such as `.pt-5` means adding large top padding. 
You can specify border using `border`. The bg-color using `bg-dark` , `bg-primary` The text color using `text-white`
You can use `.container-sm|md|lg|xl` to determine **when the container should be responsive.** The higher, it will be responsive for the bigger viewport. (eg. `-container-xxl` will stop being responsive after >=1200px but `-container-sm` will be responsive until 576 px)
### Grid System
It is built with flexbox up to **12 columns across the page**. You can group if you don't want to use 12 columns. You can create unequal columns, but it need to sum up to 12 columns. The pattern of the class is : `col-*-*` the first one represents responsiveness while second one represents a number. if the second one is not specify, bootstrap will handle the layout automatically. The grid responsiveness has six classes `.col-` or `.col-|sm|md|lg|xl|xxl|-`
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