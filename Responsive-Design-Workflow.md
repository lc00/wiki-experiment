## Overview

1. Create a content inventory
2. Make content reference wireframes
3. Design in structured text
4. Create a linear design
5. Determine breakpoints and document them with breakpoint graphs
6. Sketch and develop designs for the major breakpoints
7. Develop a web-based mockup of your design
8. Take and present screenshots of your design as your initial design presentation
9. Present and iterate on your web-based mockup for subsequent presentations
10. Create a style guide

## From The Content Out

* Start with a content inventory: A simple list of the elements that will need to be arranged on the page.
* Start with the zero interface: What would happen if a user could translate thought into reality. Anything that you add to this might be one step too many.
* If you don't have actual content, use similar content from other sites to drive discussion

## Content Reference Wireframes

* No detail- reference content, rather than depicting it
* Don't go for "the big reveal"
* Build the wireframe in HTML/CSS

Example:

1. Book title
2. Synopsis/description
3. Purchase options and formats
4. Resources
5. Errata

### Process

For each type of page:

1. Make an HTML page with the responsive meta tag
2. Start by ordering your content inventory top-to-bottom, single column. Think `<section`.
3. Style them as large blocks. Prefer words like `small` and `bold`, and use broad units like `em`s to work quicker without getting bogged down in design systems.
4. Set their heights relative to how much space they should take up.
5. Add navigation (as a single container)
6. Add media queries for tablet-ish devices (> 600px), making necessary adjustments
8. Repeat for > 900px

## Designing In Text

* "Adding accessibility" assumes UI-first, rather than content-first
* Start adding representative content, and stay open to what changes to the content inventory they might suggest

## Linear Design

* Once you have your linear design, think and sketch a little bit
* Then, make some decisions about the type for the page
* Then, make some decisions aobut the color
* Then, start applying the type and color to the CSS. No gradients, shadows, columns, or radii
* Then, add any images
* Then, add any forms
* Test on actual devices

A design language consists of:

* Layout (general usage and composition of space and elements)
* Color
* Typography
* Imagery

Design funnel:

1. Define values & goals
2. Discover moods and metaphors
3. Generate ideas, define a concept
4. Create a visual language
5. Design

## Breakpoint Graphs

* Start thinking about style guides

You may need a breakpoint for:

* Visual design and layout
* Functionality
* Content

You'll probably need 2-3 major breakpoints, you'll probably never need more than 4.

### Graph Elements

* Horizontal line is for a quantitative scale (like device width)
* Bands are for qualitative ranges (like which stylesheets apply)
* Mark each breakpoint with a bullet and a label
* Put thumbnail layouts under band

### Steps

1. Draw a horizontal line and bound it
2. Make some guesses at major breakpoints, and label them
3. Add thumbnail sketches
4. Add minor breakpoints (no major layout changes)
5. Adds bands

## Designing For Breakpoints

* Generate a ton of thumbnail sketches, as many as you can in 15 minutes
* Pick 3 to explore more
* Each one should be about a page, with annotations
* You can put scans of the sketches as CSS backgrounds to help with layout
* Think about classes of devices with major breakpoints

Consider these in particular at different sizes:

* Text
  * Column width
  * Text size
  * Touch target size on buttons
* Navigation
  * Keep mobile simple!
* Tables
  * Small (keep)
  * Blockable (make each row a block-level element)
  * Charatable (turn into a data visualization)
  * Difficult (come up with another plan)

## Creating a Web-Based Design Mockup

* Start with mobile
* Expand width until something doesn't look or feel right, then add a breakpoint
* Coordinate this with your breakpoint graph

Connect all the files together with a static site generator.

## Presentation, Round One: Screenshots

Be careful about sharing the static site with a client. You'll want to talk about the visual design, they'll make inferences about the interaction design. It allows you to get feedback early without implying you're farther along than you are. Take screenshots at each of your major breakpoints. You might consider scripting the screenshots with a headless browser. Present with a projector or large screen to make it easy for everyone to see. You can also put them in a slide deck.

## Presentation, Round Two: In the Browser

Your site should never look _broken_, even if it doesn't look _perfect_. Demo on actual devices. Still downplay the functionality and focus mainly on the layout. Consider linking pages from a table of contents instead of in the app. Considering taking notes on the app in the app itself with localStorage + contenteditable.

## Creating Design Guidelines

The web mockups don't communicate the design system; make a web-based one. Include:

* Design philosophy and background information
* Layout / grid system
* Typography
* Color and texture
* Imagery (illustrative and photographic)

Consider organizing your style guide by component.

* Screenshots of page layouts should be available, and generating them should be automatic
* Code snippets should update themselves
* Code snippets should be syntax highlighted
* Include your breakpoint graph
