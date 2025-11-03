---
{"dg-publish":true,"permalink":"/2-areas/programming/web/w3-school-css-form/","tags":["w3school"],"created":"2025-10-12T11:55:39.326+07:00","updated":"2025-10-12T15:59:25.705+07:00"}
---

CSS form can be greatly improved with CSS
Some commonly used CSS properties for styling input fields, are:
- width
	- used to set width of input field. can use attribute selector to select specific input type such as `input[type=text] { }`
	- When applying the `width` by default it is WIDTH + PADDING + BORDER which will causes overflow (padding and border are added outside that width). You have to add `box-sizing: border-box` so the width included only padding and border.  #webrevision 
- padding
	- used to add some space inside text field.
- margin
- border and border-radius
	- used to change border size and color
- background-color and color
	- used to add background color and text color
- font-size


> [!NOTE] About `padding` and `width`
> You can specify top bottom / left and right in just 1 line such as
> `margin: 4px 2px;` this mean 4px space above and below the button AND 2px to the left and right of it.

## Style input with focus
By default, browsers may add blue outline around the input when it gets focus (clicked on) You can remove this by adding `outline: none;`
You can use `:focus` selector to do something with the input field when it gets focus such as
`input[type=text]:focus { background-color: lightblue; }`

## Style input with icon/image
```css
input[type=text] {  
	background-color: white;  
	background-image: url('searchicon.png');  
	background-position: 10px 10px;  
	background-repeat: no-repeat;  
	padding-left: 40px;
}
```

## Animated Search Input
```css
input[type=text] {  transition: width 0.4s ease-in-out;}  
input[type=text]:focus {  width: 100%;}
```
This use [[CSS Transitions\|CSS Transitions]]

## Style Text Area
`<textarea></textarea>` has the grabber, you can remove this by adding `resize: none;`
