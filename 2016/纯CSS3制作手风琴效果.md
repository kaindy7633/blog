> 使用CSS3制作手风琴效果

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
	<style>
		.accordionMenu {
			background-color: #fff;
			color: #424242;
			font: 12px Arial, Verdana, sans-serif;
			margin: 0 auto;
			padding: 10px;
			width: 500px;
		}
		.accordionMenu h2 {
			margin: 5px 0;
			padding: 0;
			position: relative;
		}
		.accordionMenu h2:before {
			border: 5px solid #fff;
			border-color: #fff transparent transparent;
			content: "";
			height: 0;
			position: absolute;
			right: 10px;
			top: 15px;
			width: 0;
		}
		.accordionMenu h2 a {
			background: #8f8f8f;
			background: -moz-linear-gradient(top, #cecece, #8f8f8f);
			background: -webkit-gradient(linear, left top, left bottom, from(#cecece), to(#8f8f8f));
			background: -webkit-linear-gradient(top, #cecece, #8f8f8f);
			background: -o-linear-gradient(top, #cecece, #8f8f8f);
			background: linear-gradient(top, #cecece, #8f8f8f);
			border-radius: 5px;
			color: #424242;
			display: block;
			font-style: 13px;
			font-weight: normal;
			margin: 0;
			padding: 10px 10px;
			text-shadow: 2px 2px 2px #aeaeae;
			text-decoration: none;
		}
		.accordionMenu :target h2 a,
		.accordionMenu h2 a:focus,
		.accordionMenu h2 a:hover,
		.accordionMenu h2 a:active {
			background: #2288dd;
			background: -moz-linear-gradient(top, #6bb2ff, #2288dd);
			background: -webkit-gradient(linear, left top, left bottom, from(#6bb2ff), to(#2288dd));
			background: -webkit-linear-gradient(top, #6bb2ff, #2288dd);
			background: -o-linear-gradient(top, #6bb2ff, #2288dd);
			background: linear-gradient(top, #6bb2ff, #2288dd);
			color: #fff;
		}
		.accordionMenu p {
			margin: 0;
			height: 0;
			overflow: hidden;
			padding: 0 10px;
			-moz-transition: height 0.5s ease-in;
			-webkit-transition: height 0.5s ease-in;
			-o-transition: height 0.5s ease-in;
			transition: height 0.5s ease-in;
		}
		.accordionMenu :target p {
			height: 100px;
			overflow: auto;
		}
		.accordionMenu :target h2:before {
			border-color: transparent transparent transparent #fff;
		}
	</style>
</head>
<body>

	<div class="accordionMenu">
		<div class="menuSection" id="brand">
			<h2><a href="#brand">Brand</a></h2>
			<p>Lorem ipsum dolor...</p>
		</div>
		<div class="menuSection" id="promotion">
			<h2><a href="#promotion">Promotion</a></h2>
			<p>Lorem ipsum dolor sit amet...</p>
		</div>
		<div class="menuSection" id="event">
			<h2><a href="#event">Event</a></h2>
			<p>Lorem ipsum dolor sit amet...</p>
		</div>
	</div>

</body>
</html>
```
