# Standards

This is just a quick list of the standards and best practices that will be employed in this styleguide (and in developing the site in general).

## HTML/CSS Naming and Specificity

For HTML/CSS naming and specificity, we will follow the BEM methodology, which stands for Block, Element, Modifier. The general idea behind BEM is explained very well [here](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/), but can be boiled down to this: there are layers inside your application, full of single-responsibility and reusable modules. The best example is the example given inside this article; you have, for instance, a person. A person is a whole, reusable element; it is what's considered a `block`. You have, on that person, a hand; a hand is a part of the person. This is known as an `element`. You also have different types of hands; a left one, and a right one. That is known as a `modifier`. Be careful, though, as some elements are blocks in their own right; your hand could also be considered a block, as it contains smaller elements like 'finger' and 'palm'.

When in doubt, nest blocks. For example, you might have:

```html
<div class="header">
  <div class="header__logo-area logo-area">
    <img src="logo.png" class="logo-area__logo" />
    <h1 class="logo-area__text">Test</h1>
  </div>
</div>
```

The idea behind this standard is to have the simplest, easiest to understand CSS classes, so having blocks within blocks helps with that some, otherwise your class names get a little unreal :)

The idea behind this standard is to also **not be specific**, so the point is to use **only one class** when setting up your CSS. For example, using the above:

```css
.header { /* ... */ }
.logo-area { /* ... */ }
.logo-area--left { /* ... */ }
.logo-area__logo { /* ... */ }
.logo-area__text { /* ... */ }
```

This helps **immensely** keep your CSS maintainable; no longer do you have to chain six classes to get the exact condition you want.

## CSS Ordering and Commenting

In general, keep your CSS files neat and orderly. Start from the top of the page/element visually and work your way down; make appropriate headers to denote what section of the block/element you are working on. For example:

```css
/* === HEADER === */
.header { /* ... */ }
.logo-area { /* ... */ }
...

/* === MAIN CONTENT === */
.content { /* ... */ }
.entry { /* ... */ }
...

/* === SIDEBAR === */
.sidebar { /* ... */ }
.sidebar--left { /* ... */ }
...

/* === FOOTER === */
.footer { /* ... */ }
...
```

This will help keep the code organized and easy to understand. Additionally, the headers make it easier to find what you're searching for; in Vim, I can find `FOOTER` with only a few keystrokes!

## General CSS Standards

In general, follow [this guide](http://codeguide.co/) for how to order your elements, and for general CSS rules. It's long, but worth scanning; for some highlights:

* Break your CSS rules into sections: Positioning, Block Model, Typography, Visual, Etc.
* Inside each section, list your rules in alphabetical order
* **Never** use shorthands; i.e. use `margin-left` instead of just `margin`, as this will prevent you from setting properties that don't need to be set
* Single declaration rules go on one line; for instance: `.logo-area__text { font-size: 16px; }`
* You should rarely need to use ids or element names. In general, **don't**
* No line break between related items; for nested items, one line break between rules and first nested rule, e.g.:
```css
.header {
  font-size: 16px;

  &:hover { font-size: 18px; }
}
.logo-area {
  display: block;
  float: left;
}
```

## General SCSS Standards

In general, follow [this guide](https://css-tricks.com/sass-style-guide/). Important highlights:

* Maximum nesting is 3 levels deep
* Extends and includes first
* 2 spaces (no tabs)
* Use all CSS style guide rules!
* Nest breakpoint rules inside of original rules for ease of finding/editing

## Conclusion

That's about all, folks! If you follow these standards and stick to the general ideas, we'll be much better off. No worries if you're unsure about following some of this -- BEM can be a bit abstract sometimes :) If you have any questions or concerns about this, please don't hesitate to reach out to me. I'll be happy to help!
