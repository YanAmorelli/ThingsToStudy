# SASS
**Main differences between sass and css**

**1. Variables:** You can create a variable and pass the value on css properties. 

``` Scss
  $font-stack: Helvetica, sans-serif;
  
  body {
  font: 100% $font-stack;
  }
 ```
 
 ``` css
 body {
  font: 100% Helvetica, sans-serif;
}
```

* As you can see, you don't need to repeat the same font again and again. You just need to create a variable and pass the value. So, it's easier to padronize. 

**2. Modules:** You don't need to write all your css in a unique file. It's possible to create partials and use that in another file. Like the sample below:

``` scss
// _base.scss
$font-stack: Helvetica, sans-serif;
$primary-color: #333;

body {
  font: 100% $font-stack;
  color: $primary-color;
}

// styles.scss
@use 'base';

.inverse {
  background-color: base.$primary-color;
  color: white;
}
```

``` css
body {
  font: 100% Helvetica, sans-serif;
  color: #333;
}

.inverse {
  background-color: #333;
  color: white;
}
```

* A good use case for this "_base.scss" is to create  in the root of your frontend and use to padronize styles and maybe to create a responsive style. 

* TODO: Search responsive style and scss.

**3. Mixins:** It's helps you code to be very dry (don't repeat yourself principle). You can create an "object" of css properties and call it in your classes. Like the example below:

``` scss
@mixin theme($theme: DarkGray) {
  background: $theme;
  box-shadow: 0 0 1px rgba($theme, .25);
  color: #fff;
}

.info {
  @include theme;
}
.alert {
  @include theme($theme: DarkRed);
}
.success {
  @include theme($theme: DarkGreen);
}
```

``` css
.info {
  background: DarkGray;
  box-shadow: 0 0 1px rgba(169, 169, 169, 0.25);
  color: #fff;
}

.alert {
  background: DarkRed;
  box-shadow: 0 0 1px rgba(139, 0, 0, 0.25);
  color: #fff;
}

.success {
  background: DarkGreen;
  box-shadow: 0 0 1px rgba(0, 100, 0, 0.25);
  color: #fff;
}
```

* This is beatiful! You only use "@include theme" and if the theme isn't the default you pass as parameter and that's it. It's easier.
* Obs.: You could use extend/inheritance in some code parts, but I think that the "@include" property is enough

**4. Operators:** In sass you don't need to do math. You just set the operations and sass do it for you. Like in this example below: 

```scss
@use "sass:math";

.container {
  display: flex;
}

article[role="main"] {
  width: math.div(600px, 960px) * 100%;
}

aside[role="complementary"] {
  width: math.div(300px, 960px) * 100%;
  margin-left: auto;
}
```

```css
.container {
  display: flex;
}

article[role="main"] {
  width: 62.5%;
}

aside[role="complementary"] {
  width: 31.25%;
  margin-left: auto;
}

```
5. Source: [Every code in here was copied in sass guide](https://sass-lang.com/guide)
