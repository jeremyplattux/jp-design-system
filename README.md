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
