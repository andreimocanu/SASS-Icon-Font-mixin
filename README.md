# SASS Icon font generator

An easy to use mixin for generating icon fonts (font css and icon classes).

A custom icon font requires many lines of codes and constant updates if you keep expending the project.

I created a very handfull way of generating the code so you can save a lot of time.

<h3>Usage</h3>

<pre>
$font-icons: (
	icon1-name : icon1-code,
	icon2-name : icon2-code,
);
@include font-icons($map, $class, $family, $file, $cache);
</pre>

The mixin will generate 2 chunks of code:

1. The @font-face initialization
2. The CSS classes used by the font

Here are the 5 options:
$map    - the map that contains the font icons (variable)
$class  - the font class name; ex: icon (string)
$family - the font family name; ex: mocanu (string)
$file   - the font files location; VERY IMPORTANT: please include the full path except the file extensions; the mixin will generate the code using the 4 @font-face formats: eot, ttf, woff and svg; ex: http://www.mywebsite.com/fonts/font-file (string)
$cache  - the cache variable; should be updated everytime you make changes in the font file (string)

All the icon classes are auto generated from the $font-icons map, so you only have to add them there.

<h3>Usage</h3>

<pre>
$font-icons: (
	close : '\e900',
	edit : '\e901',
	next : '\e902',
	prev : '\e903',
);
@include font-icons('icon', $font-icons, 'iconfont', 'http://www.mywebsite.com/fonts/font-file', 'vi573');
</pre>

<h3>Result</h3>

<pre>
@font-face {
	font-family: 'iconfont';
	src: url('http://www.mywebsite.com/fonts/font-file.eot?#vi573');
	src: url('http://www.mywebsite.com/fonts/font-file.eot?#vi573#iefix') format('embedded-opentype'),
	     url('http://www.mywebsite.com/fonts/font-file.ttf?#vi573') format('truetype'),
	     url('http://www.mywebsite.com/fonts/font-file.woff?#vi573') format('woff'),
	     url('http://www.mywebsite.com/fonts/font-file.svg?#vi573#dreamstime') format('svg');
}
.icon {
    font-family: 'iconfont' !important;
    speak: none;
    font-style: normal;
    font-weight: normal;
    font-variant: normal;
    text-transform: none;
    line-height: 1;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
.icon--close::before {
    content: '\e900';
}
.icon--edit::before {
    content: '\e901';
}
.icon--next::before {
    content: '\e902';
}
.icon--prev::before {
    content: '\e903';
}
</pre>
