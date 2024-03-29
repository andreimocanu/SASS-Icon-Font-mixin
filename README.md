# SASS Icon font generator

An easy to use mixin for generating icon fonts (font css and icon classes).

If you use an app like iconmoon to create your custom icon font, you can export the css also in .scss format, but that code is not very optimized.

I created a very handful way of generating the code so you can save a lot of time.

The mixin will generate 2 chunks of code:

1. The @font-face initialization
2. The CSS classes used by the font

<h3>Options</h3>

<strong>$map</strong> - the map that contains the font icons

<strong>$class</strong> - the font class name; ex: icon

<strong>$family</strong> - the font family name; ex: mocanu

<strong>$file</strong> - the font files location; VERY IMPORTANT: please include the full path except the file extensions; the mixin will generate the code using the 4 @font-face formats: eot, ttf, woff and svg; ex: http://www.mywebsite.com/fonts/font-file

<strong>$cache</strong> - the cache variable; should be updated everytime you make changes in the font file

All the icon classes are auto generated from the $font-icons map, so you only have to add them there.

<h3>Usage</h3>

<pre>
$font-icons: (
	close : '\e900',
	edit : '\e901',
	next : '\e902',
	prev : '\e903',
);
@include font-icons($font-icons, 'icon', 'my-font', 'http://www.mywebsite.com/fonts/font-file', 'vi573');
</pre>

<h3>Result</h3>

<pre>
@font-face {
	font-family: 'my-font';
	src: url('http://www.mywebsite.com/fonts/font-file.eot?#vi573');
	src: url('http://www.mywebsite.com/fonts/font-file.eot?#vi573#iefix') format('embedded-opentype'),
	     url('http://www.mywebsite.com/fonts/font-file.ttf?#vi573') format('truetype'),
	     url('http://www.mywebsite.com/fonts/font-file.woff?#vi573') format('woff'),
	     url('http://www.mywebsite.com/fonts/font-file.svg?#vi573#dreamstime') format('svg');
}
.icon {
    font-family: 'my-font' !important;
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
