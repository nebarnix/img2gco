# img2gco
Image to reprap gcode converter

See http://wiki.nebarnix.com/wiki/Img2gco for overall project details!

Todo:
- [ ] Implement bi-directional etching
- [ ] Finish calibration script (currently left dangling who knows what state its in)
- [ ] Add areas that are above the white clip boundary to preview where skip-overs will be 

Usage details:
* Laser Min Power [0-255]: - This is the laser power that corresponds to WHITE
* Laser Max Power [0-255]: - This is the laser power that corresponds to BLACK
* Laser 'Off' Power [0-255]: - This is the laser power that will not mark the wood at all, even if it just sits there. Usually this is the bare minimum that your PWM board will respond to.
* Skip over values above [0-255]: This defines the white level. In a JPEG the white level probably contains some compression artifacts so you might have to go down to 252 or so. PNG images should have white at 255 so 254 is a good value. (TODO: preview the image with this level hi-lighted)
* Travel (noncutting) Rate [mm/min]:" - Slewing between places speed.
* Scan (cutting) Rate [mm/min]: - Speed to move while lasering. This is usually limited by the commands per second rate of your firmware, you can go faster from an SDcard than over USB. You will need to find this speed, and note that the power levels will need tweaked if this speed is changed.
* Overscan Distance (prevents twang from showing) [mm]: - This sets a 'blank' distance before the start of the line to give the belts time to settle down and the motors to reach constant speed.
* Height (width autocalculated) [mm]: - set the height, the script will autosize the width. (TODO: add an either/or option)
* Horizontal Resolution [mm/pixel]: - mm between pixels. If you make this larger you can attain faster speeds, but at the price of some detail loss. 0.1 is really amazing 0.15 is nearly so. 0.2 starts to look a little fuzzy. Beyond that you will probably see pixelization.
* Scangap [mm/line]: - This is the distance between lines which is a function of your laser spot size. You need to make this small enough so there aren't visible unburned lines. For my laser this is 0.05 though I can usually get away with 0.075 because its faster. 0.1 leaves visible lines, which is kind of a cool effect. You can try to defocus your laser to make thicker lines for shorter overall total time, but you will have to increase your power. Note that if lines start to overlap you might need to bring your power down slightly.
* Start X [mm from 0 for right of image]: - X value to start image from. The laser will start here and move in the positive direction as it scans.These X,Y points correspond to the *top right* of the image.
* Start Y [mm from 0 for top of image]: - Y value to start image from. The laser will start here and move in the positive direction as it scans.These X,Y points correspond to the *top right* of the image.
