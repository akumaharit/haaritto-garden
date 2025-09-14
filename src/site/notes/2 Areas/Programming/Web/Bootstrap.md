---
{"dg-publish":true,"permalink":"/2-areas/programming/web/bootstrap/","created":"2024-10-16T22:02:38.181+07:00","updated":"2025-09-02T22:50:12.584+07:00"}
---

You can easily load bootstrap using CDN
- a CDN for loading resources like Bootstrap helps improve the performance and reliability of your website by leveraging a network of distributed servers.
- however, if you use CDN you can't customize the CSS. if you want to customize, you have to download as it will give you SaSS files.
- there are CSS and JS bundle (some components will require the CSS bundle.)
- prior to bootstrap 5.0 you will have to include jQuery? to load the JS bundle.
``` html
CSS
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

JS Bundle
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" integrity="sha384-MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script>
```
