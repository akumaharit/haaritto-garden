---
{"dg-publish":true,"permalink":"/2-areas/programming/web/client-side-rendering/","created":"2026-01-25T14:00:08.043+07:00","updated":"2026-01-25T14:09:56.718+07:00"}
---

Instead of generating HTML on the server side, **browser send in raw data and the browser or client use that raw data to generate the appropriate HTML.**

On the server side, the returning HTML response for GET request should include: (this will convert the JSON, the javascript object into string.)
```html
<script>
let items = ${JSON.stringify(items)}
</script>
```
When view source the HTML file browser received you will see:
```html
<script>
let items = [{"_id":"696c6641d1559bc220f5b372","text":null},{"_id":"696c6b78ac37591b3a9c9f34","text":"Test56"},{"_id":"696c6b7aac37591b3a9c9f35","text":"awrtaw"},{"_id":"696c6b7bac37591b3a9c9f36","text":"aw45aw45r"},{"_id":"696cb9bd480bd02416272c2f","text":"Test2"},{"_id":"69734fca8aeb10f0d1dc8f5a","text":"Test"},{"_id":"69734fcd8aeb10f0d1dc8f5b","text":"Hello"},{"_id":"6973501487a3e5ccdaa62230","text":"asdasd"},{"_id":"6973501787a3e5ccdaa62231","text":"asdsad"}]
</script>
```
That mean, the variable has been created in global scope, it can be used for any statement run on the client side.
