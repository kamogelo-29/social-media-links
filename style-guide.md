# Front-end Style Guide

## Purpose

This style guide gives you a complete visual system for the Social links profile challenge. Use it as a reference for spacing, typography, colors, and responsive layout.

## Layout

- Design widths:
  - Mobile: 375px
  - Desktop: 1440px
- Keep the card centered on the page.
- Mobile card width: full width with safe padding (`16px` or `24px`).
- Desktop card width: fixed max width around `380px` to `420px`.
- Use a consistent spacing rhythm: `8px`, `16px`, `24px`, `32px`.

## Color palette

- Primary green: `hsl(75, 94%, 57%)`
- White: `hsl(0, 0%, 100%)`
- Dark grey (page background): `hsl(0, 0%, 8%)`
- Card grey: `hsl(0, 0%, 12%)`
- Soft text grey: `hsl(0, 0%, 20%)`

### Usage

- Page background: dark grey `hsl(0, 0%, 8%)`.
- Card background: slightly lighter dark grey `hsl(0, 0%, 12%)`.
- Primary text: white.
- Secondary text: soft grey.
- Accent and interactive highlights: green.

## Typography

- Font family: `Inter`, fallback `system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`.
- Font weights:
  - `400` for regular body text
  - `600` for labels, location, and button text
  - `700` for the profile name heading

### Recommended sizes

- Body text: `14px`, line-height `1.6`
- Profile name: `28px`, line-height `1.1`, weight `700`
- Location: `15px`, weight `600`
- Quote/bio: `15px`, weight `400`, line-height `1.7`
- Social links: `15px` or `16px`, weight `600`

## Card component

- Container:
  - Background: dark grey `hsl(0, 0%, 12%)`
  - Border radius: `30px`
  - Padding: `24px`
  - Optional shadow: soft glow or subtle shadow for depth
- Avatar:
  - Shape: circle
  - Size: `90px` to `100px`
  - Optional border: thin white or soft ring for separation
- Name:
  - Large, bold, and eye-catching
- Location:
  - Smaller, muted grey, with medium weight
- Quote/bio:
  - Easy to read at body size with generous spacing

## Social links

- Layout:
  - Mobile: stack links vertically
  - Desktop: optional horizontal row or centered group
- Button style:
  - Background: transparent or lightly tinted
  - Border radius: `20px`
  - Padding: `14px 18px`
  - Text align: center
- Hover / focus:
  - Hover background or border highlight with green accent
  - Focus: clear visible ring using green, for accessibility

## Spacing guide

- Small gap: `8px`
- Standard gap: `16px`
- Large gap: `24px`
- Extra large gap: `32px`

Use these values for vertical spacing between sections and horizontal spacing between buttons.

## Accessibility

- Ensure high contrast between text and the dark background.
- Use visible focus styles for interactive links.
- Provide `alt` text for avatars.
- Use semantic HTML for the card and link elements.

## Responsive hints

- Start with a mobile-first layout.
- Avoid fixed widths on small screens; use responsive padding instead.
- Center the card with `margin: 0 auto`.
- Keep the desktop card narrow enough to feel like a profile panel.

## Practical CSS notes

- Base page styles:
  - `html { font-family: Inter, sans-serif; font-size: 14px; }`
  - `body { background-color: hsl(0, 0%, 8%); color: #fff; margin: 0; min-height: 100vh; display: grid; place-items: center; padding: 24px; }`
- Card styles:
  - `background-color: hsl(0, 0%, 12%); border-radius: 30px; padding: 24px;`
- Link styles:
  - `display: block; text-decoration: none; color: inherit; border-radius: 20px; padding: 14px 18px; transition: background-color 0.2s ease, transform 0.2s ease;`
  - `:hover` / `:focus` should use the green accent and be easy to see.

> This guide is designed to help you build the Social links profile page with a consistent, polished style across mobile and desktop.
