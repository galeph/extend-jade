Extend Jade
===========

Extension for jade, a mixins

## Install

## Use

## [Bolierplate](http://html5boilerplate.com/)
```jade
extend .../templates/html5-bolierplate

block head
    +Meta(false, { "title" : "Example", "description" : "This is a description" })
    title Example!

block stylesheet
    +normalize('2.7.0')
    +css('/myStyle.css')

block body
    +ie-simple(true, 5, false )
        p Use IE 5

block scripts
    +modernizr('2.10')
    +JQuery('1.8', 'js/')
    +GoogleAnalytics('UA-XXXXXXX')
```
Render
```html
<!DOCTYPE html>
<html class="no-js">
	<head>
		<meta charset="utf-8"/>
		<meta http-equiv="X-UA-Compatible" content="IE=edge"/>
		<meta name="viewport" content="width=device-width, initial-scale=1"/>
		<link rel="shortcut icon" href="favicon.ico"/>
		<meta property="og:title" content="Example" />
		<meta property="og:type" content="This is a description" />
		<title>Example!</title>
		<link rel='stylesheet' href='//cdnjs.cloudflare.com/ajax/libs/normalize/2.7.0/normalize.min.css'/>
	</head>
	<body>
		<![if IE 5]>
			<p>Use IE 5</p>
		<![endif]>
		<script src='//cdnjs.cloudflare.com/ajax/libs/modernizr/2.10/modernizr.min.js'></script>
		<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.8/jquery.min.js"></script>
		<script>window.jQuery || document.write('<script src=http://code.jquery.com/jquery-1.8.min.js><\/script>');</script>
		<script>window.jQuery || document.write('<script src=http://ajax.aspnetcdn.com/ajax/jQuery/jquery-1.8.min.js><\/script>');</script>
		<script>window.jQuery || document.write('<script src=js/1.js><\/script>');</script>
		<script type="text/javascript">
		(function(b,o,i,l,e,r){b.GoogleAnalyticsObject=l;b[l]||(b[l]=
			function(){(b[l].q=b[l].q||[]).push(arguments)});b[l].l=+new Date;
			e=o.createElement(i);r=o.getElementsByTagName(i)[0];
			e.src='//www.google-analytics.com/analytics.js';
			r.parentNode.insertBefore(e,r)}(window,document,'script','ga'));
			ga('create','UA-XXXXXXX');ga('send','pageview');
		</script>
	</body>
</html>
```

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
+MetaBasic()
// MetaData
+MetaData(JSON-LD, OGP, others)
//- See http://json-ld.org/
//- See http://opengraphprotocol.org/
+MetaData({
      "@context": "http://json-ld.org/contexts/person.jsonld",
      "@id": "http://dbpedia.org/resource/John_Lennon",
      "name": "John Lennon",
      "born": "1940-10-09",
      "spouse": "http://dbpedia.org/resource/Cynthia_Lennon"
    },{
        "title" : "My movie! :)",
        "type" : "video.movie",
        "url" : "http://www.imdb.com/title/...",
        "image" : "http://ia.media-imdb.com/images/..."
    },{
        "OtherProperty" : "OtherContent"
    })
```
Render
```html
<!-- MetaBasic-->
<meta charset="utf-8"/>
<meta http-equiv="X-UA-Compatible" content="IE=edge"/>
<meta name="viewport" content="width=device-width, initial-scale=1"/>
<link rel="shortcut icon" href="favicon.ico"/>
<!-- MetaData-->
<meta property="og:title" content="My movie! :)" />
<meta property="og:type" content="video.movie" />
<meta property="og:url" content="http://www.imdb.com/title/..." />
<meta property="og:image" content="http://ia.media-imdb.com/images/..." />
<meta property="OtherProperty" content="OtherContent" />
<script type="application/ld+json">{
    "@context": "http://json-ld.org/contexts/person.jsonld",
    "@id": "http://dbpedia.org/resource/John_Lennon",
    "name": "John Lennon",
    "born": "1940-10-09",
    "spouse": "http://dbpedia.org/resource/Cynthia_Lennon"
}
</script>
```
## Lib
In the JADE
```jade
// Modernizr
+modernizr('2.10', pathz)
// Jquery
+JQuery('1.8', 'js/')
// normalize
+normalize('1.0.0')
```
Render
```html
<!-- modernizr-->
<script src='//cdnjs.cloudflare.com/ajax/libs/modernizr/2.10/modernizr.min.js'></script>
<!-- JQuery-->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.8/jquery.min.js"></script>
<script>window.jQuery || document.write('<script src=http://code.jquery.com/jquery-1.8.min.js><\/script>');</script>
<script>window.jQuery || document.write('<script src=http://ajax.aspnetcdn.com/ajax/jQuery/jquery-1.8.min.js><\/script>');</script>
<script>window.jQuery || document.write('<script src=js/1.js><\/script>');</script>
<!-- normalize-->
<link rel='stylesheet', href='//cdnjs.cloudflare.com/ajax/libs/normalize/1.0.0/normalize.min.css'<
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
