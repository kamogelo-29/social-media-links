# Frontend Mentor - Social links profile solution

This is my solution to the [Social links profile challenge](https://www.frontendmentor.io/challenges/social-links-profile-UG32l9m6dQ).

## Overview

### The challenge

The goal was to build a social links profile card that matches the supplied design and allows users to see hover and focus states for the interactive links.

The page contains:

- A profile image
- A profile name
- A location
- A short biography
- Social media links
- A Frontend Mentor attribution

### Links

- Live Site URL: https://kamogelo-29.github.io/social-media-links/
- GitHub: https://github.com/kamogelo-29

## My process

### 1. Starting with the mobile design

I approached the project from the supplied 375px mobile design and tried to make the layout fluid enough to respond to larger screen sizes.

Instead of relying entirely on fixed pixel values, I experimented with relative units and CSS functions such as `em`, `vw`, `vh`, `min()`, and `clamp()`.

This project was an important exercise in understanding that responsive design is not only about adding media queries. Some properties should scale naturally, while other properties need to change when the layout itself needs to change.

### 2. Component structure

I kept the page structure simple and semantic:

- `<main>` contains the social profile card.
- `<img>` displays the profile image with alternative text.
- `<h1>` identifies the profile name.
- `<p>` elements provide the location and biography.
- `<ul>` and `<li>` elements group the social links.
- `<a>` elements provide the interactive destinations.
- `<footer>` contains the Frontend Mentor attribution.

### 3. CSS design system

I used CSS custom properties for the main colors so that the repeated design decisions were defined in one place:

```css
:root {
    --body-bg: hsl(0, 0%, 8%);
    --primary-green: hsl(75, 94%, 57%);
    --text-color: hsl(0, 0%, 100%);
    --card-bg: hsl(0, 0%, 12%);
    --soft-text-grey: hsl(0, 0%, 20%);
}
```

This helped me begin thinking about CSS variables as design decisions rather than simply individual values.

### 4. Responsive strategy

One of the main goals of this project was learning how to make a component respond between the mobile and desktop designs.

I used:

- `min()` to limit the card width:
  `width: min(85%, 400px);`
- `clamp()` to experiment with fluid typography.
- `em` for sizing that can relate to the element's font size.
- A media query for larger-screen layout changes.

The important lesson was learning to distinguish between **fluid changes** and **structural changes**.

Fluid changes can often be handled with relative units or CSS functions. Structural changes are better candidates for media queries.

## Built with

- Semantic HTML5
- CSS custom properties
- CSS Flexbox
- CSS logical properties such as `margin-block`, `margin-inline`, `padding-block`, and `padding-inline`
- Responsive design
- Relative CSS units
- `min()`
- `clamp()`
- CSS media queries
- Custom `@font-face` font loading
- Mobile-first workflow

## What I learned

### CSS custom properties

I learned how CSS variables can represent decisions from a design system:

```css
:root {
    --primary-green: hsl(75, 94%, 57%);
}
```

Then the variable can be reused:

```css
color: var(--primary-green);
```

This makes it easier to keep repeated values consistent and change them from one place.

### `min()`

I used:

```css
.social-link-card {
    width: min(85%, 400px);
}
```

This was one of my most useful responsive-design decisions in the project.

It allows the card to use a percentage on smaller screens while preventing it from becoming wider than `400px`.

### `clamp()`

I experimented with `clamp()` for typography:

```css
.user_name {
    font-size: clamp(1.9em, 3vw, 2em);
}
```

This helped me understand the idea of a value having a minimum, a preferred fluid value, and a maximum.

I also learned that `clamp()` should not be added simply because a property is responsive. It is most useful when I actually want a value to scale gradually within defined limits.

### Logical properties

I practiced properties such as:

```css
margin-block
margin-inline
padding-block
padding-inline
```

This helped me move away from thinking only in terms of `top`, `right`, `bottom`, and `left`.

### Responsive design

The biggest lesson from this project was that responsive design is a combination of:

1. Fluid sizing
2. Sensible maximum and minimum limits
3. Layout systems such as Flexbox
4. Media queries when the structure actually needs to change

I am still developing my ability to decide which technique is appropriate for each situation.

## Challenges and how I approached them

### Challenge 1: Translating a visual design into CSS

I did not have a professional design tool or designer specification to measure from. I initially estimated dimensions visually and adjusted the CSS until the result looked close to the reference.

This taught me that implementation becomes easier when I first identify the design system: container size, spacing, typography, colors, and layout relationships.

### Challenge 2: Making the card responsive

I initially used different card sizing strategies for smaller and larger screens.

During review, I recognized that a component should not automatically receive completely different sizing rules just because the reference design has a mobile and desktop version.

A better approach is to allow the component to remain fluid where possible and introduce a breakpoint only when the layout genuinely needs to change.

### Challenge 3: Choosing CSS units

I experimented with `em`, `vw`, and `vh`, but this also showed me that responsive units need to be chosen based on the relationship I want.

For example:

- `rem` is useful for values tied to the root sizing system.
- `em` can be useful for component-relative sizing.
- `%` is useful when a value should relate to its containing block.
- `vw` relates to viewport width.
- `vh` relates to viewport height.

I learned that choosing a relative unit is not automatically better; the unit should match the behavior I want.

### Challenge 4: Deciding when to use media queries

I initially treated the supplied desktop width as a reason to redesign the component at a breakpoint.

I am learning instead to ask:

> At what width does the current layout stop working?

That makes the breakpoint a consequence of the layout rather than an arbitrary device size.

## Review notes and improvements for future versions

After reviewing this implementation, there are several areas I would improve.

### 1. Avoid making the desktop card `22%` wide

The desktop rule currently uses:

```css
.social-link-card {
    width: 22%;
}
```

This makes the card depend heavily on viewport width.

A more stable approach would be to keep a fluid width with a sensible maximum, for example:

```css
.social-link-card {
    width: min(85%, 400px);
}
```

This also reduces the need to maintain separate width rules for mobile and desktop.

### 2. Avoid using `100vw` when normal block sizing is enough

The current implementation uses the viewport height correctly for centering, but the layout can generally rely on the normal width of the containing block instead of explicitly forcing `100vw`.

For full-height layouts, `min-height: 100vh` is often a better starting point than forcing an element to be exactly the viewport width.

### 3. Reconsider the body font-size change

The desktop media query changes:

```css
font-size: xx-small;
```

This makes the base text smaller on larger screens.

That is usually the opposite of the responsive behavior I would want here. It would be better to establish an intentional typography scale and only change individual elements when the design requires it.

### 4. The `clamp()` ranges need careful checking

The location rule currently uses:

```css
font-size: clamp(0.975em, 1vw, 0.8em);
```

The minimum is larger than the maximum. That defeats the intended `clamp()` range.

A `clamp()` should normally follow the mental model:

```text
minimum ≤ preferred value ≤ maximum
```

So this is an important bug to correct.

### 5. Avoid `vh` for typography unless viewport height is actually relevant

The biography uses:

```css
font-size: clamp(0.84em, 2.5vh, 0.875em);
```

Using viewport height means the text size can change when the viewport height changes, even when the available horizontal space has not changed.

For typography, `rem`, `em`, `vw`, or a combination such as `clamp()` with an appropriate fluid value may be more predictable.

### 6. The avatar should have a controlled size

The avatar currently uses:

```css
width: 25%;
```

Because the card itself changes width, the avatar changes with it.

A controlled size, potentially using a fixed or bounded value, would make the profile image more predictable.

### 7. Improve interactive states

The challenge specifically asks for hover and focus states.

The current stylesheet defines a hover state, but the next version should also explicitly consider keyboard focus:

```css
.social-media-links:focus-visible {
    /* visible keyboard focus styling */
}
```

This is an accessibility improvement and an important part of making interactive components production-ready.

### 8. Keep transitions on the base state

Instead of putting the transition only on the hover rule:

```css
ul > li > a:hover {
    transition: all 0.3s ease-in-out;
}
```

the transition can be placed on the base link:

```css
ul > li > a {
    transition: background-color 0.3s ease-in-out,
                color 0.3s ease-in-out;
}
```

This makes the transition apply consistently when entering and leaving the hover state.

## Continued development

I want to continue improving:

- Responsive layout reasoning
- Flexbox and Grid
- CSS custom properties and design tokens
- `clamp()`, `min()`, `max()`, and `calc()`
- Logical CSS properties
- Accessibility and ARIA
- Keyboard navigation and focus states
- CSS animations and transitions
- Component-based CSS architecture
- Building layouts from a design specification instead of estimating everything visually

I also want to become more confident explaining **why** I chose a particular CSS property or unit, rather than only knowing how to write it.

## AI Collaboration

I used ChatGPT as a learning and development assistant during this project.

The collaboration was focused on understanding the reasoning behind the implementation rather than simply copying generated code. ChatGPT helped me:

- Review my responsive-design decisions.
- Understand when to use `min()` and `clamp()`.
- Think about the difference between fluid changes and structural layout changes.
- Review CSS units such as `em`, `rem`, `%`, `vw`, and `vh`.
- Identify areas where my media-query strategy could be improved.
- Discuss CSS custom properties as part of a design system.
- Review accessibility and interactive-state considerations.
- Turn the challenges I encountered into learning objectives.

The implementation was still my learning exercise: I wrote the HTML and CSS, tested the result, made design decisions, and used the review process to understand what could be improved.

## Acknowledgments

- [Frontend Mentor](https://www.frontendmentor.io/) for providing the challenge and design.
- ChatGPT for acting as a learning and code-review assistant throughout the project.

## Author

- GitHub: [@kamogelo-29](https://github.com/kamogelo-29)
