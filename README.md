#CSS Coding Guidelines (style guide)
---

Table of Contents:

- [Formatting](#formatting)
- [Naming Conventions](#naming)
- [Oraganization](#organization)
- [Ids vs Classes](#ids-classes)
- [Selectors](#selectors)
- [Comments](#comments)
- [Name-Spacing](#name-spacing)
- [Import Statements](#import)
- [Shorthand Notations](#shorthand)

## <a id="formatting"></a>Formatting

In instances where a rule set includes only **one declaration**, consider removing line breaks for readability and faster editing. Any rule set with multiple declarations should be split to separate lines.

**Right**
```css
.div1 { width: 100px; }
.foo { margin: 20px; }

.bar { 
  border: 1px solid #000;
  color: #ccc;
  padding: 5px; 
}

.foobar { border-radius: 5px; }
```

**Wrong**
```css
.profile-header { background-color: #999; color: #111; margin: 20px; }

.div5 {
  overflow: auto;
}
```

CSS rules should be comma seperated but live on new lines:

**Right:**
```css
.content,
.content-edit {
  …
}
```

**Wrong:**
```css
.content, .content-edit {
  …
}
```

CSS blocks should be seperated by a single new line. not two. not 0.

**Right:**
```css
.content {
  …
}
.content-edit {
  …
}
```

**Wrong:**
```css
.content {
  …
}

.content-edit {
  …
}	
```


## <a id="naming"></a>Naming Conventions

Classes and IDs are lowercase with words separated by a dash (although you shouldn't be using IDs...)

**Right:**
```css
.user-profile {}
.post-header {}
#top-navigation {}
```

**Wrong:**
```css
.userProfile {}
.postheader {}
#top_navigation {}
```

Image file names are lowercase with words separated by a dash:

**Right:**
```
icon-home.png
```

**Wrong:**
```
iconHome.png
icon_home.png
iconhome.png
```

Image file names are prefixed with their usage.

**Right:**
```
icon-home.png
bg-container.jpg
bg-home.jpg
sprite-top-navigation.png
```

**Wrong:**
```
home-icon.png
container-background.jpg
bg.jpg
top-navigation.png
```

## <a id="organization"></a>Organization

- Organize sections of code by component.
- Develop a consistent commenting hierarchy.
- Use consistent white space to your advantage when separating sections of code for scanning larger documents.
- When using multiple CSS files, break them down by component instead of page. Pages can be rearranged and components moved.

```css
/*
 * Component section heading
 */
 
 .top-navigation {
   ...
 } 
```

```css
/*
 * Component section heading
 *
 * Sometimes you need to include optional context for the entire component. Do that up here if it's important enough.
 */
 
 .top-navigation {
   ...
 }
```

## <a id="ids-classes"></a>IDs vs. Classes

You should almost **never need to use IDs**. Duplicate ID selectors on a page can be very bad and hard to track down. So best practice, don't use them! Stick with classes.

## <a id="selectors"></a>Selectors

- Use classes over generic element tags (`p` or `div`) for performance optimization.
- Avoid using several attribute selectors (e.g., [class^="..."]) on commonly occuring components. Browser performance is known to be impacted by these.
- Keep selectors short and strive to limit the number of elements in each selector to three.
- Scope classes to the closest parent only when necessary (e.g., when not using prefixed classes).

Right:
```css
/* Good example */
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
```
Wrong:
```css
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
```

## <a id="comments"></a>Comments
Code is written and maintained by people. Ensure your code is descriptive, well commented, and approachable by others. Great code comments convey context or purpose. Do not simply reiterate a component or class name.

Be sure to write in complete sentences for larger comments and succinct phrases for general notes.

```css
/* Bad example */
/* Modal header */
.modal-header {
  ...
}
```
```
/* Good example */
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
```

## <a id="name-spacing"></a>Name-spacing

Name-spacing is great! But it should be done at a component level – never at a page level.

Also, namespacing should be made at a descriptive, functional level. Not at a page location level. For example, `.profile-header` could become `.header-hero-unit`.

**Wrong:**

```css
.nav,
.home-nav,
.profile-nav,
```

**Right:**

```css
.nav,
.nav-bar,
.nav-list
```
	
## <a id="import"></a>Import Statements
Compared to `<link>`s, `@import` is slower, adds extra page requests, and can cause other unforeseen problems. Avoid them and instead opt for an alternate approach:

* Use multiple `<link>` elements.
* Compile your CSS with a preprocessor like Sass or Less into a single file
* Concatenate your CSS files with Grunt or some other task runner.

**Right:**
```
<!-- Use link elements -->
<link rel="stylesheet" href="core.css">
```
**Wrong:**
```
<!-- Avoid @imports -->
<style>
  @import url("more.css");
</style>
```

## <a id="shorthand"></a>Shorthand Notation

Strive to limit use of shorthand declarations to instances where you must explicitly set **all** the available values. Common overused shorthand properties include:

* `padding`
* `margin`
* `font`
* `background`
* `border`
* `border-radius`

**Right:**
```css
.element {
  margin-top: 20px;
  margin-bottom: 10px;
  background-color: red;
  background-image: url("image.jpg");
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
}
```
**Wrong:**
```css
.element {
  margin: 20px 0 10px 0;
  background: red;
  background: url("image.jpg");
  border-radius: 3px 3px 0 0;
}
```

*Note: Much inspiration for this is borrowed from others. [mdo](http://codeguide.co/) in particular*
