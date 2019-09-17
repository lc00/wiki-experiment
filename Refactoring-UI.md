## Starting From Scratch

Start with a feature, not an app shell or layout for what you imagine future features will be. Detail comes later- no typefaces, shadows, icons, colors, etc. Make spacing, contrast, and size do the heavy lifting. Don't design too much. Don't imply functionality in your design that you aren't going to build.

Choose a personality:

* Expensive/sophisticated: Gold
* Elegant/classic: serif
* Serious/formal: No border radius
* Official/professional: less personal tone
* Safe/familiar: Blue
* Neutral: small border radius
* Friendly: more casual language
* Playful: sans-serif, large border radius
* Fun/Not Serious: Pink

Limit your choices by designing systems in advance. To size something, compare 3 options from your system and see which one feels better.

* Font size
* Font weight
* Line height
* Color
* Margin
* Padding
* Width
* Height
* Box shadows
* Border radius
* Border width
* Opacity

## Hierarchy is everything

Semantic hierarchy doesn't have to _also_ be visual hierarchy. A lot of section titles are treated more like secondary labels. Primary actions should be obvious, secondary actions should be clear but not prominent, tertiary actions should be discoverable but unobtrusive.

* Instead of emphasizing something, try de-emphasizing the things around it instead
* Destructive actions don't need to be red- they can have low hierarchy and a confirmation.
* Labels are a last resort, try using context, format, and supporting text instead
* Deemphasize labels, unless the label will be the thing the person is looking for.
* Things are semantically similar (like buttons for actions) doesn't mean they should have the same hierarchy.

Font size isn't everything. Relying too much on size makes primary content too large and secondary content that's too small- use color and weight instead.

### Color

3 Colors:

* Dark for primary content (like the headline of an article)
* Grey for secondary content (like the date an article was published)
* Lighter grey for tertiary cotent (like a copyright notice)

### Weight

2 Weights:

* Normal (400-500) for most text
* Heavier (600-700) for text you want to emphasize

Weights less than 400 only work for headings.

### Contrast

* Grey on a colored background reduces contrast too much; hand-pick a color with the same hue and lower saturation/lightness.
* Icons use a lot of pixels, which ups the weight. You can compensenate by reducing contrast. You can also thicken a line instead of changing the contrast.

## Layout and Spacing

Start with too much white space- going the other way encourages you to stop when something isn't actively bad, rather than good. Establish a spacing and sizing system. At the small end, they need to be closer together. No two values in the scale should be closer than about 25%.

Practical scale:

* 4px
* 8px
* 12px
* 16px
* 24px
* 32px
* 48px
* 64px
* 96px
* 128px
* 192px
* 256px
* 384px
* 512px
* 640px
* 768px

You don't have to fill the whole screen- if you only need 600px, use 600px. 400px is a good starting place for mobile and you won't have to grow it as much as you think. You can use columns instead if you need to grow something.

Grids are overrated- sometimes elements should have a fixed width instead. Even if you adapt the grids, the size of something jumps around as you add and remove columns. Use max-width and min-width instead.

Relative sizing (width/height, padding, margin) doesn't scale- big stuff scales more than small stuff. Hand-pick sizes for different scales.

Avoid ambiguous spacing- related things should be closer (vertical and horizontal). Related things should have more space around them than within them.

## Designing Text

Establish a type scale. You can't use a purely mathematical scale because you end up with fractional values and need enough sizes close to your baseline. Try:

* 12px
* 14px
* 16px
* 18px
* 20px
* 24px
* 30px
* 36px
* 48px
* 60px
* 72px

Use good fonts. Helvetica is a good default sans-serif. Never use a typeface with less than 5 weights (filter by 10+ to account for italics). Fonts for headlines have tight letter-spacing and shorter x-height, and opposite for body fonts.

* Keep your line length in check- 20-35em is a good way to constrain the line length.
* Align mixed type sizes by their baseline, not center.
* Line-height is proportional- shorter line lengths/larger sizes need less height, longer line lengths/smaller sizes needs more.
* Not every link needs a color- you can emphasize something with a heavier weight or darker color, or only underlining on hover if it's not as important.
* Align with readability in mind- don't center long-form text (longer than 2-3 lines), right-align numbers, hyphenate justified text, left-align everything else.
* Use letter-spacing effectively- tighten headlines, letter-space all-caps to account for lack of variance in x-height.

## Working with Color

### Colors you need

* Primary Colors
    * Primary actions, active navigation elements
    * One, maybe 2
    * 5-10 lighter and darker shades
    * Dark shades for text
    * Ultra-light shades for tinted backgrounds on alerts
* Accent colors
    * Eye-grabbing color like Yellow/pink/real to highlight something, plus shades
    * Red + shades for confirming destructive states
    * Yellow + shades for warnings
    * Green + shades to highlight a positive trend
* Greys
    * Text, backgrounds, panels, form controls, almost everything in an interface
    * You want 8-10 shades
    * True black feels unnatural, so start with a really dark grey and work your way up to light

### How to define shades

* Choose your base color first (middle value). Should be something that would work well as a button background.
* Pick your darkest and lightest shade. Darkest is heading text, lightest tints backgrounds of elements. You can use an alert box to test. Start with same hue as base and adjust saturation and lightness.
* Fill in the gaps. 5-10 shades per color, 9 is good. Start with (100) 300 (500) 700 (900), should be right in the middle. Fill in (100) 200 (300) 400 (500) 600 (700) the same way.
* Don't let lightness kill your saturation- You need more saturation at the lighter and darker ends of lightness. 
* Hue 60, 180, and 300 are light, dark hues are 0, 120, and 240. You can make something appear lighter or darker by rotating the hue no more than 20-30 degrees toward the lighter or darker peak. 

### How to define greys

* Do 9 greys, same process. Darkest should be darkest text, lightest should be an off-white background.
* Greys don't have to be grey- saturation makes some greys feel cool (blues) and others warm (yellow or orange).

---

White on colored backgrounds is hard to make accessible, especially if the colors are lighter. You can help contrast by doing dark colored text on light colored text. If the backgrounds are dark, you can create hierarchy beyond white by rotating the hue. Don't rely on color alone- you can use contrast instead of just completely different colors.

## Creating Depth

Emulate a light source- light comes from above. Decide whether the element should be raised or inset, and how much. Choose the shadow color by hand instead of just using white, or you'll suck the saturation out of the underlying color. A couple of pixels is plenty, and should have a pretty sharp edge. Text input and boxes are often inset. 

Use Shadows to convey elevation- lots of blur on a large shadow is high, not much blur on a small shadow is low. Small shadows are good for being noticeable but not dominate like buttons, medium shadows are good for dropdowns, large shadows are good for modals. Create 5 shadows- start with largest and smallest. Shadows are great for interaction, like drag and drop, where the element should feel like it was lifted off the page. You can also make something feel like it was pressed by manipulating or removing the shadow.

Shadows can have two parts: The first is large and soft and is the shadow from direct light, the second is small, tight, and dark, and comes from indirect light. As something lifts off your page, the direct light should get bigger, and the indirect light should eventually disappear. 

Even flat designs can have depth- dark colors feel "back", and light colors feel "front." You can also use solid shadows.

Overlap elements to create layers, which also transitions between two areas. You can join or overflow. When overlapping images, consider putting a small border that matches the background around it to prevent clashing.

## Working with Images

Use good photos- professional, stock, or unsplash.

Text needs consistent contrast- reduce the contrast of the background image by making it lighter, darker, lower contrast, or washed in a color. To colorize an image, lower its contrast, desaturate it, and add a solid fill with the "multiply" blend mode. This can also help tie it in with brand colors. A wide, blurred, non-offset shadow makes the text sit on top too.

Everything has an intended size- even if it's a vector, it will have too much or too little detail at the wrong size. Don't shrink screenshots, because it will make your content too hard to read. Use a mobile view, use a screenshot of small area, or remove all the detail. Simplify icons for favicons.

Beware user-uploaded content. Control the size and shape of their images, center/cover them, use subtle inner box shadows or transparent borders to help them stand out from the background

## Finishing Touches

Supercharge the defaults- replace bullets with icons, styled quotes for testimonials, different colors/weights/underlines for links, custom checkboxes and radio buttons with the brand color.

Add color with accent borders to make a bland element have some life. You can put accent borders across the top of a card, under an active navigation item, on the side of an alert message, as a short accent under a headline, or across the top of the entire layout.

Decorate your backgrounds by changing the color (especially good for emphasizing a particular panel), adding a slight gradient (2 hues that are no more than 30 degrees apart), a repeating pattern (across the entire background, across a single edge) with low contrast, or by adding simple shapes and illustrations (with low contrast).

Don't overlook empty states- these are opportunities to grab attention, explain, and promote. Create a call-to-action to encourage them to take the next step. Don't have options and chrome for a bunch of actions a user can't take yet.

Use fewer borders- they make a layout very busy and cluttered. Box shadows often accomplish the same thing in a more subtle way, or by giving them different background colors, or adding more space.

Dropdown menus and tables don't have to just be a dry list of links- you can use multiple columns, supporting text, and colorful icons. Cells in tables can have hierarchy, color, and images. Radio buttons can be selectable cards.

## Leveling Up

Look for decisions on sites you wouldn't have made yourself. Rebuild your favorite interfaces.
