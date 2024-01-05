# Intro

We (as web developers) should care about users with disabilities. We should make sure our websites are accessible for everyone. But how do we do that? How do we make this part of our workflow?

## Reduced motion first

Lets start with reduced motion. Some people have motion sickness and other issues with moving elements on the screen. If you are going to use animations, make sure they can be disabled.

In the past I wrote my code with animations and when the product owner asked the team to work on accessibility, we had to go back and remove all the animations. This is not a good approach because it makes your code messy and more difficult to read. Doing this when the product is almost finished will create a lot of extra work. You need to check every animation and make sure it is disabled for users with motion sickness. It's easier to start with the reduced motion option and then add animations later. Same goes for other accessibility features.

A tip for your workflow is to start with the reduced motion option. This will help you to start by writing code that is accessible for everyone. Then you can add animations and other fancy stuff later.

By starting with the reduced motion option, I mean you don't add animations at all. You start by writing your code without animations, so only the functionality is there. Then you add the animations when the user has `no-preference` option enabled.

We can use the `prefers-reduced-motion` media query to detect if the user has enabled the "reduce motion" option in their operating system. If the user has enabled this option, you can disable animations and other moving elements on your website.

The `prefers-reduced-motion` media query has two options - `no-preference` and `reduce`. The `no-preference` option is the default one, and it means that the user has not enabled the "reduce motion" option. The `reduce` option means that the user has enabled the "reduce motion" option.

What should you do if the user has enabled the "reduce motion" option? You should disable animations and other moving elements on your website. But how do you do that in a clean way?

## How to use prefers-reduced-motion media query

Here a tip on how to use `prefers-reduced-motion` media query:

We start by writing our code without animations, so only the functionality is there. Then we add the animations when the user has `no-preference` option enabled.

For example, we have a selector that applies opacity. For users with `no-preference` we want to add an animation that will make the element fade in and out. For users with `reduce` option enabled we don't want to animate the element at all.

First we write our code without animations:

```css
.my-selecter {
  opacity: 0;
}

.my-selector.show {
  opacity: 1;
}
```

Then we add the animation when the user has `no-preference` option enabled:

```css
@media (prefers-reduced-motion: no-preference) {
  .my-selector {
    transition: opacity 0.3s ease-in-out;
  }
}
```

Putting it all together:

```css
.my-selecter {
  opacity: 0;
}

.my-selector.show {
  opacity: 1;
}

/* Apply animation for users that have not set their preference */
@media (prefers-reduced-motion: no-preference) {
  .my-selector {
    transition: opacity 0.3s ease-in-out;
  }
}
```
