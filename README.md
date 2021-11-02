# Personal Design System
author: Jeremy Platt

## CSS Variables
color-palette.css, typography.css, layout.css

Design systems establish design patterns that can be reused.  I employ css variables to reuse and implement system wide design changes on my personal website.
I establish the inital global variable:

(css)

`:root{
	--global-variable: value;
}`

then reference it later

(css)

`section.instance {
	width: var(--global-variable);
}`

now I can just change the variable and it will effect everywhere I use it.  I can also specifiy instances where it should be different and have it populate through.

`@media screen and (min-width: 37.5em) {
	--global-variable: value2;
}`

## Color
### HSL Responsive Color Palette
color-palette.css

By defining colors through hue, saturation and lightness level, we can easily define colors in relation to each other. In addition to this benefit, we can specify the lightness level in order to create better contrast for color blindness.

In the following palette, I set an inital primary hue then calculate additional hues by moving defined distances around the 360 color wheel while keeping the saturation and lightness the same.
/*  Color Palette Hues  */
`
  --primary-hue: 330;
  --secondary-hue: calc( var(--primary-hue) + 50 );
  --primary-comp-hue: calc( var(--primary-hue) + 200 );
  --secondary-comp-hue: calc( var(--primary-hue) + 260 );
`

From there, I change the saturation and lightness to create different color profiles for each palette choice. These include one where the saturation is changed to be a 'highlight/accent' color, and two others defined by how light or dark in the lightness level while keeping the hue and saturation the same as the original palette.

(css)
/*  Color Palette Saturation  */
/*  Color Palette Lightness Levels  */
` 
  --sat-default: 75%;
  --sat-light: 50%;
  --sat-dark: 50%;
  --sat-sat: 75%;
   
  --light-default: 80%;
  --light-light: 99%;
  --light-dark: 20%;
  --light-sat: 60%;
`
  /*  Color Palette HSL (Hue Saturation Lightness)  */
`--color-primary: hsl(var(--primary-hue), var(--sat-default), var(--light-default)); `

By defining everything as css varibles, we can easily change our color selections later, define it dependant by device/etc, or dark/light mode.

/*  Default Layout Color Palette  */

`
   --palette-ground: var(--color-primary); /*  60% of layout color */
`

### Gradients for Washes and Accents

Gradients are primarily used as image washes and element accents and are 2 to 3 analogous color combinations of the 'highlight' palette.

Example (css) /*  Color Palette Gradient Example   */

`
:root{
  --gradient-primary: 0.25turn, var(--color-secondary), var(--color-primary), var(--color-secondary-comp);
  --underwash: var(--gradient-primary);
}
.show-gradient {
      background-image: -webkit-linear-gradient(var(--underwash));
      background-image: -moz-linear-gradient(var(--underwash));
      background-image: linear-gradient(var(--underwash));
}`


### SVG Filter to Glaze Images

By using SVG filters, we can glaze images and enhance/reduce the color in our images to fit our color palette without making the image 'flatter' or 'washed' out like when we use gradient or solid color washes.  The SVG is embeded right under the body initialization in the HTML file and the filter id within is referenced within css as a url filter.

Example (in HTML):

`<svg id="svgfilters" aria-hidden="true" style="position: absolute; width: 0; height: 0; overflow: hidden;" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
    <defs>
			<filter id="underglaze" x="-10%" y="-10%" width="120%" height="120%" filterUnits="objectBoundingBox" primitiveUnits="userSpaceOnUse" color-interpolation-filters="linearRGB">
				<feColorMatrix type="matrix" values=".33 .33 .33 0 0
            .33 .33 .33 0 0
            .33 .33 .33 0 0
            0 0 0 1 0" in="SourceGraphic" result="colormatrix"/>
				<feComponentTransfer in="colormatrix" result="componentTransfer">
			    <feFuncR type="table" tableValues="0.3 0.9 0.9"/>
					<feFuncG type="table" tableValues="0.4 0.3 0.5"/>
					<feFuncB type="table" tableValues="0.9 0.6 0.3"/>
					<feFuncA type="table" tableValues="0 1"/>
		  	</feComponentTransfer>
				<feBlend mode="soft-light" in="componentTransfer" in2="SourceGraphic" result="blend"/>
			</filter>
		</defs>
   </svg>`
   
   (in CSS)
   
   `filter: url('#underglaze');`
