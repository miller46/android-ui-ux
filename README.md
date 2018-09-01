## Google Resources

[Android App Development Home](http://developer.android.com/index.html) - Nice hub of documents and guides for all things Android.  Contains resources for design, development and app store distribution.

[Design Resources](http://developer.android.com/design/index.html)

[App Store Listing Resources](http://developer.android.com/distribute/users/your-listing.html)

[Intro to Material Design](https://www.google.com/design/spec/material-design/introduction.html)

[Android Material Design Patterns](https://www.google.com/design/spec/patterns/navigation.html#) - Similar to above, but a little more Android specific.

[(Material) Design from iOS to Android](https://design.google.com/articles/design-from-ios-to-android/)  - This guide touches on designing for both platforms and some of the differences between the two.

## UI

### Material Design

Material Design as the standard guide for layouts in Android.  Starting with the Lollipop release (Android 5.0) there is native support for material design components, shadows, and animations.  There is some support for pre-Lollipop devices but some components or elements must be faked or approximated for older devices.  An example of this is elevation.  Starting with Lollipop I can declare the elevation of an item and it will automatically be drawn with a shadow and with the appropriate Z-index relative to other items.  This is not possible pre-Lollipop and any shadows and z-index will have to be done explicitly to show up on older devices.

[Android Material Design Components](https://www.google.com/design/spec/components/bottom-navigation.html#bottom-navigation-specs) - NOTE: there is no generic 'Componenets' landing page and this page starts at 'bottom navigation'.  To go to other components you can click 'Next' all the way at the bottom or click the nav drawer and find the other components.

### Designing for multiple screen sizes

Android devices are divided into generalized size and density classes to simplify designing for multiple screen sizes.  There are size classes but Android has moved away from using them too much relating to design.  Density is much more relevant.

Type               | MDPI (Baseline) | HDPI | XHDPI | XXHDPI | XXXHDPI
------------------ | ----------------| ---- | ----- | ------ | ------
Scale              | 1x              | 1.5x | 2x    | 3x     | 4x
DPI                | ~160 dpi     | ~240dpi | ~320 dpi | ~480 dpi | ~640 dpi


Market share for various screen sizes and densities (as of April 4th 2016)

       | ldpi |	mdpi |	tvdpi |	hdpi  |	xhdpi  |	xxhdpi |	Total
 ----- | ----- | ---- | ----- | ----- | ------ | ------- | ------
Small  | 2.4% | 		 |			  |       |        |         | 2.4%
Normal |      | 4.9% | 0.1%   |	41.5%	| 23.9%	 | 14.9%	 | 85.3%
Large	 | 0.3%	| 4.6% | 2.2%	  | 0.5%  | 0.5%   | 		     | 8.1%
Xlarge |		  | 3.2% |        |	0.3%	| 0.7%   |         | 4.2%
Total	 | 2.7%	| 12.7% | 2.3%	| 42.3% |	25.1%	 | 14.9%   |

For reference, size classes are as follows

* xlarge screens are at least 960dp x 720dp
* large screens are at least 640dp x 480dp
* normal screens are at least 470dp x 320dp
* small screens are at least 426dp x 320dp


Some icon sizes for various densities

Type               | MDPI (Baseline) | HDPI | XHDPI | XXHDPI | XXXHDPI
------------------ | ----------------| ---- | ----- | ------ | ------
App Launcher icons | 48px            | 72 px | 96 px  | 144 px  | 192 px 
Action Bar icons   | 32px (24px inset*)| 48 px | 64 px  | 96px | 128 px
Notification icons | 24px (22px inset*)| 36 px | 48px   | 72px | 96px

*inset here just means a padding.  So for MDPI, a 24px notification icon has content that is 22px big with 2px padding.  This requirement began with Lollipop (Android 5.0) and icons will not show up if they do not follow this structure.

Each generalized size and density spans a range of actual screen sizes and densities. For example, two devices that report a screen density of hdpi might have real pixel densities that are slightly different. Android makes these differences abstract to applications, so you can provide UI designed for the generalized sizes and densities and let the system handle any final adjustments as necessary. 

### Density-independent Pixels (dp or dip) vs Scale-independent Pixels (sp) vs Pixels (px)

The short description is that you should always use dp to make layouts consistent across multiple devices, with the only exception being for font size in which you should use sp.

Density-independent Pixels - An abstract unit that is based on the physical density of the screen. These units are relative to a 160 dpi (dots per inch) screen, on which 1dp is roughly equal to 1px. When running on a higher density screen, the number of pixels used to draw 1dp is scaled up by a factor appropriate for the screen's dpi. Likewise, when on a lower density screen, the number of pixels used for 1dp is scaled down. The ratio of dp to px will change with the screen density, but not necessarily in direct proportion. Using dp units (instead of px units) is a simple solution to making the view dimensions in your layout resize properly for different screen densities. In other words, it provides consistency for the real-world sizes of your UI elements across different devices.

Scale-independent Pixels - This is like the dp unit, but it is also scaled by the user's font size preference. It is recommend you use this unit when specifying font sizes, so they will be adjusted for both the screen density and the user's preference.

Pixels - Corresponds to actual pixels on the screen. This unit of measure is not recommended because the actual representation can vary across devices; each devices may have a different number of pixels per inch and may have more or fewer total pixels available on the screen.

More info about screen sizes and density can be found [here](http://developer.android.com/guide/practices/screens_support.html).

### Assets

There are 2 approaches for delivering assets that look good at every screen size.

1) Provide an asset with appropriate scale factor for every screen density (see chart above for scale factor).  The appropriate asset will be rendered for the phone's density class and no auto-scaling will occur.  Note that this is required for launcher and notification icons.  This is recommended for full screen images as well for performance reasons.

2) Provide a sufficiently large image and let Android scale the image automatically.  If the Android system does not find an image in the appropriate density class, the system will take the asset and scale it automatically if needed.  It is preferred to scale down as opposed to scaling up, so you may want to design an asset for the largest target screen and let the system scale down for the other.  Assets at 2x scale are typically sufficient and you will see almost no pixelation, although 3x may become the default as devices increase in size and larger devices increase marketshare.  

Assets should be provided in PNG format.  The naming convention for images is all lowercase and _'s between words

**Q:** _Why not use vector based images?_

**A:** Starting with Lollipop, Android now supports vector images however there are some compatibility issues with vector images for devices that are pre-Lollipop.  Unfortunately, around half of the market is pre-Lollipop.  This is something you may see in the next few years but there are too many issues for this to be viable at the moment.  

#### Designing for Android

[Various Material Design Resources](http://materialdesignblog.com/)

#### Inspiration

[Android Niceties](http://androidniceties.tumblr.com/)

## UX

[Google's Android UX recommendations](http://developer.android.com/training/best-ux.html)

[Do's and Don't's for Android and iOS](http://developer.android.com/design/patterns/pure-android.html)

#### Android version marketshare (as of April 22, 2016)

Android SDK version  | Current market share 
-------------------- | ----------------
5.0-5.1 Lollipop     | 35.6%            
4.4 KitKat           | 34.8%
4.1 - 4.3 Jelly Bean | 20%
6.0 Marshmallow      | 6.1%
4.0.x ICS            | 1.7%
2.3 Gingerbread      | 1.6%
2.2 Froyo            | 0.1%
3.0-3.2 Honeycomb    | 0%
2.0-2.1 Eclair       | 0%

Another perspective 

Android SDK version  | Current market share 
-------------------- | ----------------
Lollipop or newer    | 41.7%
pre-Lollipop         | 58.3%

Marketshare by device

Android phone manufacturer | Current market share 
-------------------------- | ----------------
Samsung		      | 51.9%
LG	    		      | 6.0%
Huawei 		      | 4.4%
Sony			      | 4.2%
Motorola 		      | 4.0%
Lenovo	  		      | 3.9%
HTC 			      | 2.5%
Asus 			      | 1.8%
Alcatel		      | 1.7%
Alps 			      | 1.3%
ZTE			      | 1.2%
Micromax 		      | 1.2%
Oppo 			      | 0.9%
Xiaomi 	             | 0.9%
Blu 			      | 0.4%
Lava			      | 0.4%
Acer 	                    | 0.3%
Wiko 		             | 0.3%
Nokia 			      | 0.3%
Unknown 		      | 0.3%
