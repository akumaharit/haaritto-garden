---
{"dg-publish":true,"permalink":"/2-areas/programming/web/cs-50-web-html-and-css/","tags":["cs50web"],"created":"2024-05-03T23:10:10.039+07:00","updated":"2025-10-12T16:22:52.606+07:00"}
---

# HTML
Doctype html หมายถึง html5 (latest)

`<html lang="en">` tell browser that it is "English" language, it also tell **search engine** that the web is English

Document object model (DOM) tell how the element relate with each other
drawing DOM tree can help you illustrate the HTML in graph form, useful when working with JavaScript since it modify these DOM

`<head>` tell what important of the website, but not actually a part of website like `<body>`

## Image
`<img src="cat.jpg" alt="A cat picture" width="300">`
- src stand for "source" and alt stand for 'alternative'
- alt for screenreader and for when ระบบมันล่มแล้วให้ข้อความขึ้นแทน
- image is just a SINGLE html element that **self-closing**, มันครบถ้วนของมันแล้วจึงไม่ต้องไปใส่อะไรให้มันอีก
- when scaling width, it automatically scale height in its poportional

## Anchor
`<a href="https://google.ocm">The text that will display and the user can click to access the Google </a>`
- a = anchor
- href = hyperlink reference

## Table
{ #3c310a}


A table consist of individual rows and each rows consist of individual cells
```html
<table>
	<thead> -- stuff at the top of table
		<th>Ocean</th> -- table heading
		<th>Average Depth</th>
	</thead>
	<tbody>
		<tr> --each row
			<td> Pacific Ocean </td> -- each table data
			<td> 4,280 m </td> -- each table data
		</tr>
		
		<tr> -- this is second row
			<td> Atlantic Ocean </td>
			<td> 3,646 m </td>
		</tr>
	</tbody>
</table>
```

## [[2 Areas/Programming/Web/W3School - CSS Form\|W3School - CSS Form]]
``` html
<form>
	<input type="text" placeholder="This will display before the user select the field" name="to identy what data was submitted" required=true (actually no need to state true, it is default to true)> 
	<input name="pass" type="password" placeholder="Password"> 
	<input name="red" type="radio" value="red"> Red
	<input name="country" list="countries" placeholder="Country">
	
	<datalist id ="countries">
		<option value="Thailand">
		<option value="USA">
	</datalist>

	<input type="submit">
</form>
```
In `<form>` you can specify `action` attribute to tell the browser to submit the data into that URL. And the data is sent using `GET`
`name` is the parameter name such as the password it will be send as `URL?pass=xxxx`
By default, **the `input` is a inline element.** Convert it into block using `display: block` so it will be displayed as a new line.

In case when you wanted to customize the button label but also specify the value to be sent inside, you can use this one: (Use the `<button>` inside `<form>`) #webrevision 
```html
<form action="https://www.google.co.th/search">
  <input type="text" name="q" placeholder="Search...">

  <!-- normal search -->
  <button type="submit">Google Search</button>

  <!-- image search -->
  <button type="submit" name="udm" value="2">Image Search</button>
</form>

```

# [[0 Inbox/CSS\|CSS]]

latest = css3
you can apply styling attribute to the parent element of HTML, which will work with all the element inside that parent. That is why DOM tree can be useful

applying styling to the HTML as an "style" attribute is called in-line styling
You can link .css file to an html via `<link rel="stylesheet" href="styles.css>`
- href = hyperlink, เหมือนใช้ในการเชื่อมไปยังไฟล์อื่น ซึ่ง tag link ก็มี attribute นี้เช่นกัน

The way of selecting element is called css select

## Now we will focus on common and popular CSS properties

- `padding` ใช้ขยับไม่ให้ element ข้างใน มันติดขอบของ element นั้นมากเกินไป
- `margin` เป็นพื้นที่ว่างของรอบ ๆ element นั้นให้ห่างจาก element อื่นทั้งหมด
- To center something, use `margin: ___ auto;` `align-items` is for **flexbox**. #webrevision
- `font-family` specify font family เช่น `font-family: Arial, sans-serif` หมายถึงถ้า Arial ไม่รองรับใน Browser, then it will fall back to sans-serif
	- `font-weight`, `font-size`
	- What fonts to use? [[2 Areas/Programming/Web/Fonts Falbacks and CSS web Safe fonts\|Fonts Falbacks and CSS web Safe fonts]]
- Table
	- `border 1px solid black`
	- To specify for each table data to have border, specify the border properties of CSS for td element of HTML
	- `border-collapse: collapse;` will collapse the border to single line

## Element References
- You can add **id** to a html element, **id will be unique** and can't be duplicated
- Use # to select id in CSS
- To add some reference to multiple element without being unique, you can add **class**
- Use . to select class in CSS
- Specificity: inline > id > class > type

## CSS Selector
- There are many types of CSS selector and what mentioned in [[#Element References]] is just some of the example.
- Descendent selector is used to select a children of a certain element
- You can select attribute by `a [href="google.co.th"]{ .... }` this will select `a` element with `href` attribute of `google.co.th` and apply the styling
- There is also pseudoclass in which you can make it display a certain style in some condition such as the changing the color when the `button` element was hovered on
	- you can use `button:hover{ .... }` to set the style to this one when the button was hovered on.

## Viewport
- `<meta name="viewport" content="width=device-width, initial-scale=1.0">`
- You can use media quarries to change how the webpage render in a certain device.
```css
<style>
	@media (min-width: 600px){
		body{
			background-color: red;
		}
	}
	@media (max-width: 599px){
		body{
			background-color: blue;
		}
	}
</style>
```
- There are more media quarries than the example here. You can even check the phone orientation.

## Flexbox
- use to assist in responsive design
```css
#container{
	display: flex;
	flex-wrap: wrap;
}

#container > div{
	background-color: red;
	font-size: 20px;
	margin: 5px;
	padding: 5px;
	width: 200px;
}
```
- This is called flexbox layout but there is also **grid** layout.

## [[2 Areas/Programming/Web/Bootstrap\|Bootstrap]]
- Just follow the webpage tutorial

## SaSS
- extension end with .scss
- allow you to specify value of css with variable
- variable start with &
- the browser can't understand .scss by default, you will have to manually compile it to .css to make it understand.
	- `sass test.scss:test.css` this will compile into test.css
	- `sass --watch test.scss:test.css` this will automatically compile when scss has been updated
- SaSS also around you to nest the selector, but the standard css won't allow you to do that.
- SaSS also around you to do inheritance
By SaSS vs CSS
![Pasted image 20240728181426.png|350](/img/user/3%20Resources/Attachment/Pasted%20image%2020240728181426.png) ![Pasted image 20240728181506.png|475](/img/user/3%20Resources/Attachment/Pasted%20image%2020240728181506.png)


# Project 1

```
field1=value1&field2=value2&field3=value3...
```
This string consists of a sequence of GET Parameter