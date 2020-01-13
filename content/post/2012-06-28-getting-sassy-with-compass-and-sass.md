---
title: Getting Sassy with Compass and Sass
author: Kevin Lloyd
type: post
date: 2012-06-28T12:05:28+00:00
url: /getting-sassy-with-compass-and-sass/
thumbnail: /wp-content/uploads/css-letters.jpg
categories:
  - CSS

---
Well last night I finally took the plunge and now I don't know what it is I was waiting for all these years.

[Sass][1] enables you to create CSS with much less effort than before. It brings CSS closer to the programming language that we all wish it was.

Let's get down to some of the features.

## Sass Features

### Variables

Right now,  this is going to be the feature I make the most use of. The obvious application is with color schemes.

Imagine that your site follows some sort of color scheme (yes,  I know. A real stretch of the imagination). Your links, background images, borders, etc will all share common color definitions.

```scss
$main-color: #ce4dd6;
$style: solid;

#navbar {
  border-bottom: {
    color: $main-color;
    style: $style;
  }
}

a {
  color: $main-color;
  &:hover { border-bottom: $style 1px; }
}
```

It will generate the following code:
```scss
a {
  color: #ce4dd6; }
  a:hover {
    color: #ffb3ff; }
  a:visited {
    color: #c458cb; }
```
This is a trivial example, but imaging you decide to keep your layout but alter your colors slightly. In the old days search and replace would be the only way to go. Now we have options.

### Nesting

So you need to apply some styles to your #navbar, then to the menus within it? No problem:
```scss
#navbar {
  width: 80%;
  height: 23px;

  ul { list-style-type: none; }
  li {
    float: left;
    a { font-weight: bold; }
  }
}
```

This generates:
```scss
#navbar {
  width: 80%;
  height: 23px; }
#navbar ul {
  list-style-type: none; }
#navbar li {
  float: left; }
#navbar li a {
  font-weight: bold; }
```

The syntax just makes CSS a little better to work with, in my opinion.

### Mixins

One way to think of _Mixings_ is as _multi-line variables_. You define a block of CSS that you can reuse with one statement. Consider the following:
```scss
@mixin rounded-top {
 $side: top;
 $radius: 10px;

border-#{$side}-radius: $radius;
 -moz-border-radius-#{$side}: $radius;
 -webkit-border-#{$side}-radius: $radius;
}

#navbar li { @include rounded-top; }
#footer { @include rounded-top; }
```

Will generate:
```scss
#navbar li {
 border-top-radius: 10px;
 -moz-border-radius-top: 10px;
 -webkit-border-top-radius: 10px; }

#footer {
 border-top-radius: 10px;
 -moz-border-radius-top: 10px;
 -webkit-border-top-radius: 10px; }
```

So similarly, if you decide **all **the borders on your website need to change, you simply change the mixin and it propagates. Really slick if you ask me.

There are a host of other features, but these are the ones I've exploited in my 3 hours of plaining with this thing.

## Compass

Now down to the business of how you actually use this thing. Thus far, we've only mentioned Sass. You can accomplish a lot with just that.

[Compass][2] is essentially a Sass wrapper. It comes with some built-in mixins and you can also add plug-ins. One that I found is [Compass 960 plugin][3]. As you can assume, it adds functionality for the [960 grid framework][4] (one of my personal favorites). The biggest benefit I see to this plugin is that it brings back semantics to your classes. No need for _countainer_16_ anymore. Just imagine:
```scss
#wrap
	+grid-container
	#header
		+grid(16)
	#middle
		+grid(16)
		#left-nav
			+grid(5)
			+alpha
		#main-content
			+grid-prefix(1)
			+grid(10)
			+omega
```

### Setup

First of all, these are all Ruby Gems, so installation is a snap (even on your host):

`gem install compass`

Now go to a folder with some CSS you want to make sassy:
```bash
# Copy your original files to sass files. The syntax is identical to CSS, so no extra work needed here.
mv *.css *.scss

# Initialize compass
compass init

# modify the default config file appropriately. There are things like output style, default directories, etc.
vi config.rb

# Compile sass files to CSS
compass compile

# or continually watch the folder:
compass watch
```

In watch mode, Compass will detect any changes to your *.scss files and dynamically generate the CSS file.

I encourage everyone, even [Windows Users][5], to take a look at Compass and Sass. It will change the way you think about CSS.

 [1]: http://sass-lang.com/tutorial.html
 [2]: http://compass-style.org/help/ "Compass"
 [3]: http://rubygems.org/gems/compass-960-plugin
 [4]: http://960.gs
 [5]: http://rubyinstaller.org/ "Ruby Installer for Windows"