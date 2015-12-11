# Functions & Mixins

For this project, we'll have several functions and mixins we'll rely on to keep the code clean and clear.

## Vendor Prefix

Gone are the days of old where you had to manually prefix all your CSS properties. Now, we've got a function for that! See below:

```sass
@mixin vendor-prefix($name, $argument) {
  -webkit-#{$name}: #{$argument};
     -moz-#{$name}: #{$argument};
      -ms-#{$name}: #{$argument};
       -o-#{$name}: #{$argument};
          #{$name}: #{$argument};
}
```

This will help make quick work of prefixing your code. Use it as so:

```sass
@include vendor-prefix(transition, 'background-color .3s ease');
```

Why the quotes on the second argument and not the first? Simple, the first is only one word, so it can be passed without quotes. Anything longer should be passed in single quotes. Feel free to wrap the first argument in single quotes as well for consistency.

## Calc Rem

We're using rems for this project, with a base font size of 20px. To make the math that much simpler, I have included a function to calculate the rems based on a pixel value:

```sass
@function calc-rem($target) {
    @return ($target / $text__size--base) * 1rem;
}
```

This does all the math for you. Use it as so:

```sass
font-size: calc-rem(14);
```

Voila! Instant rems.
