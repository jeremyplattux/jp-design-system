# Personal Design System
author: Jeremy Platt

## Color
### HSL Responsive Color Palette
color-palette.css

By defining colors through hue, saturation and lightness level, we can easily define colors in relation to each other. In addition to this benefit, we can specify the lightness level in order to create better contrast for color blindness.

In the following palette, I set an inital primary hue then calculate additional hues by moving defined distances around the 360 color wheel while keeping the saturation and lightness the same.

From there, I change the saturation and lightness to create different color profiles for each palette choice. These include one where the saturation is changed to be a 'highlight/accent' color, and two others defined by how light or dark in the lightness level while keeping the hue and saturation the same as the original palette.

Gradients washes are 2 to 3 color combinations of the 'highlight' palette.

By defining everything as css varibles, we can easily change our color selections later or define it dependant by device/etc.

### SVG Filter to Glaze Images

By using SVG filters, we can glaze images and enhance/reduce the color in our images to fit our color palette without making the image 'flatter' or 'washed' out like when we use gradient washes.  The SVG is embeded right under the body initialization in the HTML file and the filter id within is referenced within css as a url filter.

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
