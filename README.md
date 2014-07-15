Extend Jade
===========

Extension for jade, a mixins

## Install

## Use


##[Conditionals](http://msdn.microsoft.com/en-us/library/ms537512%28v=vs.85%29.aspx)
In the JADE
```jade
+ie("lte IE 8")
    p lte IE 8
+ie("lte IE 8", false)
    p lte IE 8
+ie-simple(false)
    p No use IE
+ie-simple(false, 9 )
    p No use IE 9
+ie-simple(true, 5, false )
    p Use IE 5
+ie-simple('gte', 5, false )
    p Use IE >5
```
Render
```html
<!--[if lte IE 8]><p>lte IE 8</p><![endif]-->
<![if lte IE 8]><p>lte IE 8</p><![endif]>
<!--[if !IE ]><p>No use IE</p><![endif]-->
<!--[if !IE 9]><p>No use IE 9</p><![endif]-->
<![if IE 5]><p>Use IE 5</p><![endif]>
<![if gte IE 5]><p>Use IE >5</p><![endif]>
```

## Meta
In the JADE
```jade
// meta
+meta
// Jquery
+loadJQuery('1.8', 'js/')
// ogp
+ogp(ogpData)
```
Render
```html
<!-- Meta-->
<meta charset="utf-8"/>
<meta http-equiv="X-UA-Compatible" content="IE=edge"/>
<meta name="viewport" content="width=device-width, initial-scale=1"/>
<link rel="shortcut icon" href="favicon.ico"/>
<!-- JQuery-->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.8/jquery.min.js"></script>
<script>window.jQuery || document.write('<script src=http://code.jquery.com/jquery-1.8.min.js><\/script>');</script>
<script>window.jQuery || document.write('<script src=http://ajax.aspnetcdn.com/ajax/jQuery/jquery-1.8.min.js><\/script>');</script>
<script>window.jQuery || document.write('<script src=js/1.js><\/script>');</script>
<!-- ogp-->

```

## Templates
In the JADE
```jade
+template('angular')#me
    p Hello angular
+template('knockout')#me
    p Hello knockout
+template('ember')#me
    p Hello ember
```
Render
```html
<script type="text/ng-template" id="me" data-template-name="me">
  <p>Hello angular</p>
</script>
<script type="text/html" id="me" data-template-name="me">
  <p>Hello knockout</p>
</script>
<script type="text/x-handlebars" id="me" data-template-name="me">
  <p>Hello ember</p>
</script>
```
## Lorem Ipsum
In the JADE
```jade
p
    +lorem(25)
.image
    +image_lorem(150, 150)
```
Render
```html
<p>Lorem ipsum dolor sit amet. Ornare nullam libero augue erat felis nunc augue inceptos aptent. Nam cubilia commodo mauris suspendisse blandit platea feugiat conubia vulputate magna euismod lectus potenti erat.
</p>
<div class="image"><img src="http://placehold.it/150x150&amp;text=F.P.O." alt="F.P.O."/>
</div>
```
