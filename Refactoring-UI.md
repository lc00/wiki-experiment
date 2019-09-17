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

Not all elements are equal- you need to deemphasize things. Font size isn't everything. Relying too much on size makes primary content too large and secondary content that's too small- use color and weight instead.

3 Colors:

* Dark for primary content (like the headline of an article)
* Grey for secondary content (like the date an article was published)
* Lighter grey for tertiary cotent (like a copyright notice)

2 Weights:

* Normal (400-500) for most text
* Heavier (600-700) for text you want to emphasize

Weights less than 400 only work for headings. Grey on a colored background reduces contrast too much. Hand-pick a color with the same hue and lower saturation/lightness. Instead of emphasizing something, try de-emphasizing the things around it instead. Labels are a last resort, try using context, format, and supporting text instead. Deemphasize labels, unless the label will be the thing the person is looking for. Semantic hierarchy doesn't have to _also_ be visual hierarchy. A lot of section titles are treated more like secondary labels. Icons use a lot of pixels, which ups the weight. You can compensenate by reducing contrast. You can also thicken a line instead of changing the contrast. Semantics are secondary- primary actions should be obvious, secondary actions should be clear but not prominent, tertiary actions should be discoverable but unobtrusive. Destructive actions don't need to be red- they can have low hierarchy and a confirmation.

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

You don't have to fill the whole screen- if you only need 600px, use 600px. 400px is a good starting place for mobile and you won't have to grow it as much as you think. You can use columns instead if you need to grow something. Grids are overrated- sometimes elements should have a fixed width instead. Even if you adapt the grids, the size of something jumps around as you add and remove columns. Use max-width and min-width instead. Relative sizing (width/height, padding, margin) doesn't scale- big stuff scales more than small stuff. Hand-pick sizes for different scales. Avoid ambiguous spacing- related things should be closer (vertical and horizontal). Related things should have more space around them than within them.

## Designing Text

### Establish a type scale

You can't use a purely mathematical scale because you end up with fractional values and need enough sizes close to your baseline. Try:

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

Use good fonts. Helvetica is a good default sans-serif. Never use a typeface with less than 5 weights (filter by 10+ to account for italics). Fonts for headlines have tight letter-spacing and shorter x-height, and opposite for body fonts. Keep your line length in check- 20-35em is a good way to constrain the line length. Align mixed type sizes by their baseline, not center. Line-height is proportional- shorter line lengths/larger sizes need less height, longer line lengths/smaller sizes needs more. Not every link needs a color- you can emphasize something with a heavier weight or darker color, or only underlining on hover if it's not as important. Align with readability in mind- don't center long-form text (longer than 2-3 lines), right-align numbers, hyphenate justified text, left-align everything else. Use letter-spacing effectively- tighten headlines, letter-space all-caps to account for lack of variance in x-height.

## Working with Color

Ditch hex for HSL. You need more colors than you think:

* Greys
    * Text, backgrounds, panels, form controls, almost everything in an interface
    * You want 8-10 shades
    * True black feels unnatural, so start with a really dark grey and work your way up to light
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

Define your shades up front:

* Choose your base color first (middle value). Should be something that would work well as a button background.
* Pick your darkest and lightest shade. Darkest is heading text, lightest tints backgrounds of elements. You can use an alert box to test. Start with same hue as base and adjust saturation and lightness.
* Fill in the gaps. 5-10 shades per color, 9 is good. Start with (100) 300 (500) 700 (900), should be right in the middle. Fill in (100) 200 (300) 400 (500) 600 (700) the same way.
* Do 9 greys, same process. Darkest should be darkest text, lightest should be an off-white background.

Don't let lightness kill your saturation- You need more saturation at the lighter and darker ends of lightness. Hue 60, 180, and 300 are light, dark hues are 0, 120, and 240. You can make something appear lighter or darker by rotating the hue no more than 20-30 degrees toward the lighter or darker peak. Greys don't have to be grey- saturation makes some greys feel cool (blues) and others warm (yellow or orange). Accessible doesn't have to mean ugly. White on colored backgrounds is hard to make accessible, especially if the colors are lighter. You can help contrast by doing dark colored text on light colored text. If the backgrounds are dark, you can create hierarchy beyond white by rotating the hue. Don't rely on color alone- you can use contrast instead of just completely different colors.

## Creating Depth

### Emulate a light source
### Use Shadows to convey elevation
### Shadows can have two parts
### Even flat designs can have depth
### Overlap elements to create layers

## Working with Images

### Use good photos
### Text needs consistent contrast
### Everything has an intended size
### Beware user-uploaded content

## Finishing Touches

### Supercharge the defaults
### Add color with accent borders
### Decorate your backgrounds
### Don't overlook empty states
### Use fewer borders
### Think outside the box

## Leveling Up
