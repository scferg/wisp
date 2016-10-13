# Wisp

[![GitHub version](https://badge.fury.io/gh/scferg%2Fwisp.svg)](https://badge.fury.io/gh/scferg%2Fwisp)
[![Bower version](https://badge.fury.io/bo/wisp.svg)](https://badge.fury.io/bo/wisp)

> Just another sass boilerplate, but one that doesn't make me angry.

## What?

**Wisp** is a simple sass-based boilerplate that provides a good starting point for a theme. The grid system is flexible and is truely a *grid*, not to be limited by rows.

There are a few minimally opinionated base styles, such as buttons and input fields, but they can easily be overwritten.

## Why?

I found myself consistently displeased with other boilerplate and frameworks that were overly complex, too opinionated, and their grid system sucked. I haven't done extensive research and comparison, but this system is what I've used on many projects, and it works well for me.

## How to install

```bash
bower install wisp
```

or

```bash
npm install https://github.com/scferg/wisp.git
```

Include the file into your project using `@import`.

```scss
@import 'bower_components/wisp/wisp.scss';
```

## How to use

Out of the box, you're ready to start creating your theme with structural styles already in place.

### Wrapper

Most content will be contained in a `.wrapper` element, which will be horizontally centered and includes spacing to the left and right to not butt up against the edge of the browser window.

**Usage:**

```html
<div class="wrapper">...</div>
```

You can also nest wrappers, but child  will not include edge padding, so you won't get undesirable stacking paddings:

```html
<div class="wrapper"> <!-- Will have edge padding -->
	<div class="wrapper"></div> <!-- Will not have edge padding -->
</div>
```

**Modifiers:**

- `is-edgeless` - Removes edge padding
- `is-small` - Sets max width to `$wrapper-widths($small)`
- `is-medium` - Sets max width to `$wrapper-width($medium)`
- `is-large` - Sets max width to `$wrapper-widths($large)`
- `is-xlarge` - Sets max width to `$wrapper-widths($xlarge)`
- `is-center` - Vertically centers children

**Note:** Utilizes [Trimmed margins](#trim-margins)

### Section

`.section` is available for separating content into... sections. It has top and bottom paddings to ensure content is spaced appropriately, which reduce when viewing on mobile devices.

You may overwrite these variables:

- `section-padding-desktop` - Default: `80px`
- `section-padding-mobile` - Default: `$section-padding-desktop * .5`

**Note:** Utilizes [Trimmed margins](#trim-margins)

### <a name="trim-margins"></a>Trimmed margins

I often found myself constantly removing top margins for `:first-child` and bottom margins for `:last-child` to eliminate stacking margins and paddings. I wanted to set spacing on parent elements and not have children dictate that. In comes `%trim-margins`.

This removes extraneous padding from *direct* child elements only.

**Usage:**

```scss
@extend %trim-margins;
```

### Cover

Another pattern I found myself using on a regular basis, is making an element the same size as its parent. This applies the following styles:

```scss
position: absolute;
top: 0;
right: 0;
bottom: 0;
left: 0;
```

Ensure that the parent element has `position` set to anything but `static` for correct sizing and positioning.

**Usage:**

```scss
@extend %cover;
```

### Grid

Ah, the grid. It can really make or break a theming experience, both for the creator and end-user. I've created an amalgamation of different grid systems I've found over the years and the result is something that works well for me.

Columns automatically wrap to the next line, so you don't have to specify rows. You simply specify the cell size in relation to a 12-column grid. Or, if you want the columns to auto-size, just don't specify a size.

**Usage:**

```html
<div class="grid">

	<div class="cell is-4"> ... </div> <!-- Width is 1/3 (4/12) -->

	<div class="cell"> ... </div> <!-- Automatically fills rest of row -->

</div>
```

Grids can be nested to create complex layouts.

There are many ways to customize the grid.

**Grid Modifiers:**

- `.has-small-gutter` - Adds small gutter between cells
- `.has-gutter` - Adds medium gutter between cells
- `.has-large-gutter` - Adds large gutter between cells
- `.is-justifycenter` - Horizontally center cells
- `.is-top` - Aligns cells to top of rows
- `.is-center` - Aligns cells to center of rows
- `.is-bottom` - Aligns cells to bottom of rows

**Cell Modifiers:**

- `.is-top` - Aligns this cell to the top of the row
- `.is-center` - Aligns this cell to the center of the row
- `.is-bottom` - Aligns this cell to the bottom of the row
- `.is-pullright` - If this cell is less than 100% of the row's width, this will push the cell to the right
- `.is-$num` - Assigns this cell's size as a fraction of 12. `$num` should be 1-12.

You may overwrite these variables:

- `$grid-gutter-small-horizontal` - Default `12px`
- `$grid-gutter-small-vertical` - Default `20px`
- `$grid-gutter-horizontal` - Default `20px`
- `$grid-gutter-vertical` - Default `30px`
- `$grid-gutter-large-horizontal` - Default `50px`
- `$grid-gutter-large-vertical` - Default `70px`

**Note:** By default, all grid columns become full-width at `<=medium`. See [Media queries](#media-queries).

### Typography

Unopinionated typography styles are applied to `<body>`, headings, and links. Most of the variables are meant to be changed to match your theme:

- `$font-family-body` - Default `sans-serif`
- `$font-family-headline` - Default `sans-serif`
- `$font-size` - Default `16px`
- `$text-color` - `$gray-dark` (See [Colors](#colors))
- `$letter-spacing` - Larger letter spacing for headlines, etc - Default `.1em`
- `$line-height` - Default `1.65`

### Buttons

Buttons are minimally styled and are easily customized.

**Usage:**

```html
<a class="button"> ... </a>

<button class="button"> ... </button>
```

**Modifiers:**

- `.is-block` - Makes the button full-width
- `.is-small` - Reduces font size, padding, and border width (for `.is-outline`)
- `.is-large` - Increases font size
- `.is-outline` - Converts to outline-only

**Colors Modifiers:**

See [Colors](#colors).

- `.is-bg-white` - Sets background color to `#fff`
- `.is-bg-xxlightgray` - Sets background color to `$gray-xxlight`
- `.is-bg-xlightgray` - Sets background color to `$gray-xlight`
- `.is-bg-lightgray` - Sets background color to `$gray-light`
- `.is-bg-gray` - Sets background color to `$gray`
- `.is-bg-darkgray` - Sets background color to `$gray-dark`
- `.is-bg-xdarkgray` - Sets background color to `$gray-xdark`
- `.is-bg-xxdarkgray` - Sets background color to `$gray-xxdark`
- `.is-bg-primary` - Sets background color to `$brand-primary`
- `.is-bg-error` - Sets background color to `$error`
- `.is-bg-warning` - Sets background color to `$warning`
- `.is-bg-success` - Sets background color to `$success`
- `.is-bg-note` - Sets background color to `$note`
- `.is-text-white` - Sets text color to `#fff`
- `.is-text-xxlightgray` - Sets text color to `$gray-xxlight`
- `.is-text-xlightgray` - Sets text color to `$gray-xlight`
- `.is-text-lightgray` - Sets text color to `$gray-light`
- `.is-text-gray` - Sets text color to `$gray`
- `.is-text-darkgray` - Sets text color to `$gray-dark`
- `.is-text-xdarkgray` - Sets text color to `$gray-xdark`
- `.is-text-xxdarkgray` - Sets text color to `$gray-xxdark`
- `.is-text-primary` - Sets text color to `$brand-primary`
- `.is-text-error` - Sets text color to `$error`
- `.is-text-warning` - Sets text color to `$warning`
- `.is-text-success` - Sets text color to `$success`
- `.is-text-note` - Sets text color to `$note`

It's very easy to add your own button modifiers.

For background colors:

```scss
.is-bg-mynewcolor { @include button-bg($mycolor); }
```

For text colors

```scss
.is-text-mynewcolor { @include button-text($mycolor); }
```

Uses these mixins will take care of automatically creating hover and outline styles.

### Forms

Input fields are setup to look great right out of the box. They also play nice when inside a `.grid` (become 100% width of the cell).

**Usage:**

```html
<input class="input" />

<select class="input"> ... </select>

<textarea class="input"> ... </textarea>
```

### Alerts

Alerts can be used to notify the user of anything. There are multiple modifiers to change the intent of the alert.

**Usage:**

```html
<div class="alert"> ... </div>
```

**Modifiers:**

- `.has-icon` - Provides extra padding on the left for an icon. Set an icon using a font icon library of your choice and adding its class (that inserts the icon as a `::before` pseudo-element) as an additional modifier, or insert icon element as a first child.
- `.is-warning` - Sets intent to a warning. Utilizes `$warning` color.
- `.is-error` - Sets intent to an error. Utilizes `$error` color.
- `.is-success` - Sets intent to a success message. Utilizes `$success` color.
- `.is-note` - Sets intent to a neutural note. Utilizes `$note` color.

### <a name="colors"></a>Colors

There are many colors to get you started. You can overwrite any of these.

- `$gray` - Default `#666`
- `$gray-xxlight` - Default `lighten($gray, 55%)`
- `$gray-xlight` - Default `lighten($gray, 45%)`
- `$gray-light` - Default `lighten($gray, 15%)`
- `$gray-dark` - Default `darken($gray, 10%)`
- `$gray-xdark` - Default `darken($gray, 25%)`
- `$gray-xxdark` - Default `darken($gray, 35%)`
- `$error` - Default `#d22017`
- `$warning` - Default `#f9b729`
- `$note` - Default `#1e90ff`
- `$success` - Default `#25d252`
- `$brand-primary` - Default `#2979ff`
- `$social-facebook` - Default `#3b5998`
- `$social-twitter` - Default ` #1da1f2`
- `$social-linkedin` - Default `#0077b5`
- `$social-pinterest` - Default `#bd081c`
- `$social-github` - Default `#4078c0`
- `$social-google-plus` - Default `#dd4b39`
- `$social-google` - Default `#4285f4`

![Color swatches](color-swatches.png?raw=true)

### <a name="media-queries"></a>Media queries

All media queries are handled by [include-media](https://github.com/eduardoboucas/include-media). You can take advantage of it throughout your theme.

There are 3 breakpoints included:

```scss
$breakpoints: (
    small:   400px,
    medium:  800px,
    large:   1100px
);
```

Refer to [include-media](https://github.com/eduardoboucas/include-media)'s documentation on usage.

## What's included

The file structure is kept to a minimum to keep the package clean and light.

```
wisp/
├── scss/
│   ├── common/
│      ├── _base.scss
│      ├── _helpers.scss
│      ├── _mixins.scss
│      ├── _normalize.scss
│      ├── _print.scss
│      ├── _variables.scss
│   ├── components/
│      ├── _alerts.scss
│      ├── _buttons.scss
│      ├── _forms.scss
│      ├── _grid.scss
│      ├── _scaffoling.scss
│      ├── _typography.scss
├── wisp.scss
```

## Dependencies
- [include-media](https://github.com/eduardoboucas/include-media) - For grid system responsiveness.

## Credits
- [html5-boilerplate](https://github.com/h5bp/html5-boilerplate) - Basis for `_base.scss`, `_helpers.scss`, and `_print.scss`
- [normalize.css](https://github.com/necolas/normalize.css) - Basis for `_normalize.scss`.
