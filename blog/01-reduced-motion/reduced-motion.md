# Accessibility Part 1 - Reduced Motion

We, as web developers, should care about users with disabilities. We must ensure that our websites are accessible to everyone. How do we do that? How do we make this part of our development process?

A few years ago, writing 'mobile first' applications became standard practice. We would write our CSS in a way that catered to mobile users before we started looking at the CSS for desktop users. I think there should be a change in the way we write code for people with disabilities. We should be writing code in a way that is **inclusive first**!

Let's start with Reduced Motion. Some people have motion sickness and other issues with moving elements on the screen. If you are going to use animations, make sure they can be disabled.

In the past, I wrote my code with animations. However, when the product owner asked the team to work on accessibility, we had to go back and remove all the animations. This is not a good approach because it makes your code messy and more difficult to read. Doing this when the product is almost finished will create extra work. You need to check every animation and make sure it is disabled for users with motion sickness. It's easier to start with the Reduced Motion option and then add animations later. The same goes for other accessibility features.

A tip for your workflow is to start with the Reduced Motion option. This will help you start by writing code that is accessible to everyone. Then, you can add animations and other fancy stuff later.

We can use the `prefers-reduced-motion` media query to detect if the user has enabled the "reduce motion" option in their operating system. If the user has enabled this option, you can disable animations and other moving elements on your website.

The `prefers-reduced-motion` media query has two options: `no-preference` and `reduce`. The `no-preference` option is the default one, and it means that the user has not enabled the "reduce motion" option. The `reduce` option means that the user has enabled the "reduce motion" option.

What should you do if the user has enabled the "reduce motion" option? You should disable animations and other moving elements on your website. But how can this be implemented effectively?

## How to Use the `prefers-reduced-motion` Media Query

By starting with the Reduced Motion option, I mean you don't add animations at all. You start by writing your code without animations. Only the functionality is there. Then, you add the animations when the user has the `no-preference` option enabled.

We have a selector that changes the opacity when the class `show` is applied. For users with `no-preference`, we want to add a transition that will make the element fade in and out. For users with the `reduce` option enabled, we don't want to animate the element at all.

First, we write our code without animations:

```css
.my-selector {
  opacity: 0;
}

.my-selector.show {
  opacity: 1;
}
```

Then, we add the animation when the user has the `no-preference` option enabled:

```css
@media (prefers-reduced-motion: no-preference) {
  .my-selector {
    transition: opacity 0.3s ease-in-out;
  }
}
```

Putting it all together:

```css
.my-selector {
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

To help make the web accessible and usable for everyone, we, as developers, should start using accessibility features in our projects. Reduced Motion is one of the accessibility features that we can use to make the web more inclusive. It's a small effort that can make a big difference for some users.
