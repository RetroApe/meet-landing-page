# Frontend Mentor - Meet landing page solution

This is a solution to the [Meet landing page challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/meet-landing-page-rbTDS6OUR). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
- [Author](#author)

## Overview

### The challenge

- View the optimal layout depending on their device's screen size
- See hover states for interactive elements

### Screenshot

Desktop | Tablet | Mobile

<p>
<img src="meet landing page (desktop).png" height="300" hspace="15">
<img src="meet landing page (tablet).png" height="300" hspace="15">
<img src="meet landing page (mobile).png" height="300" hspace="15">
</p>

### Links

[Solution URL](https://www.frontendmentor.io/solutions/smoothly-responsive-landing-page-with-the-help-of-clamp--8dg6VkyED)

[Live Site URL](https://retroape.github.io/meet-landing-page/)

## My process

- Learn about SASS and how to install it
  - Used 'npm' of Node.js with Parcel
- Check the Figma file
- Think about the layout, choices I should make when choosing HTML elements
- Think about the possible solutions to the layout
  - Write HTML, still having layout in mind
- Go through all the colors and text presets
  - Add everything in form of variables and `@mixins`'s
- Started with Desktop; tried to match the layout as much as possible
  - First Header, then Body, then Footer
- Used `clamp` to make the page as responsive as possible
  - When page was completely responsive from Desktop to Tablet, then did the same from Tablet to Mobile

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- Desktop-first workflow
- SCSS

### What I learned

- Do NOT, I repeat, do NOT put SCSS variables under `:root`... they are not custom properties
- How to work with SCSS
  - Variables and `@mixin`'s are cool
- How to put background images and position them, while using color to to have an overlay on the image; done with `::after` and `::before`
  - starts at line 388 of `main.scss`
- How to use `clamp` for responsive design
  - You need:
    - Max and min value for clamp
    - Beginning and end of those two values, i.e. width of the screen
  - Used elementary math to write two equations with two variables and got a nice formula when solving it

So...

`clamp: (C_min, x + y, C_max)`

**W_b** - Width of the screen at the beginning

**W_e** - Width of the screen at the end

The above are known constants which you yourself decide.

Below are variables that need to be solved.

**x** - Value in pixels or `rem`

**y** - Value in `vw`

The two equations we set:

$$x = C_{min} - W_e*y$$
$$x = C_{max} - W_b*y$$

When we solve for **y**, we get:

$$y = \frac{C{max} - C{min}}{W_b - W_e}$$

Now for an example...

Let's suppose we want to have a font size of `2.5rem` at `1440px` and `1rem` at `768px`.

$$C{min} = 1rem$$ 
$$C{max} = 2.5rem$$
$$W_b = 1440px$$
$$W_e = 768px$$

First, we would need the units to be the same, so:

$$W_b = 90rem$$
$$W_e = 48rem$$

When we enter the numbers into an equeation:

$$y = \frac{2.5rem - 1rem}{90rem - 48rem}$$
$$y = 0.03571428571428571428571428571429$$
$$y \approx 0.035714$$
$$y \approx 3.5714vw$$

This is your **y**. 

For **x** you enter the numbers into one of the equations. For example:

$$x = 2.5rem - 90rem * 0.03571428571428571428571428571429$$
$$x = -0.714rem$$

When put in `clamp`:

`clamp: (1rem,  -0.714rem + 3.5714vw, 2.5rem)`

Hoping that the calculation is correct...

This way, the font size will smoothly go from its max size at 1440px screen width to its min size at 768px width.

And you can do this with padding and margins as well. Anything really.

Pretty cool!

## Author

- Frontend Mentor - [@RetroApe](https://www.frontendmentor.io/profile/RetroApe)
- LinkedIn - [@tomislavsuto81](https://www.linkedin.com/in/tomislavsuto81)
