> 纯CSS3制作3D导航栏，带立体效果和分隔

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
	<title>CSS制作立体导航</title>
	<link rel="stylesheet" href="http://www.w3cplus.com/demo/css3/base.css">
	<style>
		body{
		  background: #ebebeb;
		}
		.nav{
		  width:560px;
		  height: 50px;
		  font:bold 0/50px Arial;
		  text-align:center;
		  margin:40px auto 0;
		  background: #f65f57;
          border-radius:10px;
          box-shadow:0px 8px 0px #900;
		}
		.nav a{
		  display: inline-block;
		  -webkit-transition: all 0.2s ease-in;
		  -moz-transition: all 0.2s ease-in;
		  -o-transition: all 0.2s ease-in;
		  -ms-transition: all 0.2s ease-in;
		  transition: all 0.2s ease-in;
		}
		.nav a:hover{
		  -webkit-transform:rotate(10deg);
		  -moz-transform:rotate(10deg);
		  -o-transform:rotate(10deg);
		  -ms-transform:rotate(10deg);
		  transform:rotate(10deg);
		}

		.nav li{
		  position:relative;
		  display:inline-block;
		  padding:0 16px;
		  font-size: 13px;
		  text-shadow:1px 2px 4px rgba(0,0,0,.5);
		  list-style: none outside none;
		}

        .nav li::before,.nav li::after{
			content:"";
			position:absolute;
			top:14px;
			height: 25px;
			width: 1px;
	    }
		.nav li::after{
	        right: 0;
	        background: -webkit-linear-gradient(rgba(255,255,255,0), rgba(255,255,255,.2) 50%, rgba(255,255,255,0));
	        background: -o-linear-gradient(rgba(255,255,255,0), rgba(255,255,255,.2) 50%, rgba(255,255,255,0));
	        background: linear-gradient(rgba(255,255,255,0), rgba(255,255,255,.2) 50%, rgba(255,255,255,0));
		}
		.nav li::before{
		  left: 0;
		  background: -moz-linear-gradient(top, #ff625a, #9e3e3a 50%, #ff625a);
		  background: -webkit-linear-gradient(top, #ff625a, #9e3e3a 50%, #ff625a);
		  background: -o-linear-gradient(top, #ff625a, #9e3e3a 50%, #ff625a);
		  background: -ms-linear-gradient(top, #ff625a, #9e3e3a 50%, #ff625a);
		  background: linear-gradient(top, #ff625a, #9e3e3a 50%, #ff625a);
		}

		.nav li:first-child::before{
    		background: none;
		}

	    .nav li:last-child::after{
    		background: none;
		}

		.nav a,
		.nav a:hover{
		  color:#fff;
		  text-decoration: none;
		}

	</style>
</head>
<body>
	<ul class="nav">
    	<li><a href="">Home</a></li>
    	<li><a href="">About Me</a></li>
    	<li><a href="">Portfolio</a></li>
    	<li><a href="">Blog</a></li>
    	<li><a href="">Resources</a></li>
    	<li><a href="">Contact Me</a></li>
	</ul>
</body>
</html>
```
