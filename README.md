# Object Tracking System using Android Device - Honours Project 2016-2017


## Project Summary

### Overall Goals
The overall goal of this project is to evaluate the possibilites and limitations of an Android device for imaging and tracking of small animals such as insects. The resulting analysis should consist of a program which camn be used to extract useful data for tracking.
The final thesis will include:
- A technical evaluation of the device for tracking purposes
- A recording/tracking application prototype description (this will also be implemented)
- An evaluation of this application.


### External Libraries
This project will make use of a few external libraries:
- OpenCV4android SDK
- Color Picker by QuadFlask on GitHub. Imported as "color-picker.aar"


## Code Documentation

### Coding Convention

This summary discusses coding conventions used throughout `XML` and `Java` code.

#### ID Names
ID's are named using underscore convention, for example, `@+id/start_tracking_button`, in XML, or `R.id.start_tracking_button` in Java.

#### Layout files
All layout files in the layout folders discussed below are named using underscore convention, for example `activity_main.xml`, or `R.layout.activity_main.xml` in Java.

#### Drawable files
- All drawable files in the `drawables` folder are named using underscore convention, for example, `ic_preferences.png`. 
- All icons begin with the ic_ prefix, e.g. `ic_viewrecording.png`
- All drawables used for styling purposes are prefixed with the widget they are meant to style, such as `button_preferences.xml`
- If a drawable styles multiple widgets, it is prefixed with `widget`, e.g. `widget_gradient.xml`

#### Strings
All string resources in `strings.xml` are named using underscore convention, for example, `@string/start_tracking`, or `R.string.start_tracking` in Java.

#### Dimensions
All dimension values in `dimens.xml`are named using underscore convention, for example `@dimen/activity_horizontal_margin`

#### Colours
All colours in `colours.xml` are named using camelCase convention, for example `@color/colorAccent`

#### Styles
All styles in `styles.xml` are named using underscore convention, e.g. `@style/start_tracking_button`

#### Menus
All menu XML files in `res/menu` folder are named using underscore convention, e.g. `flash_menu.xml`
All ID's within the XML file are also named using underscore convention, e.g. `android:id="@+id/flash_auto"`.


### Layout folders

Currently, my layouts are organized into 3 different folders. This overview gives a brief summary of the purpose of each of the folders.

#### layout
The layout directory is the default layout file. When layouts are being inflated, this folder will be searched last for the layout, because it is less "specific" than the other two folders. Currently, this folder is used for mobile layouts, and tablet layouts have its own layout folders, discussed next.

#### layout-sw600dp
The sw600dp suffix stands for "smallest width 600dp". From Android Documentation describing smallest width: 
> The Smallest-width qualifier allows you to target screens that have a certain minimum width given in dp. For example, the typical 7" tablet has a minimum width of 600 dp, so if you want your UI to have two panes on those screens (but a single list on smaller screens), you can use the same two layouts from the previous section for single and two-pane layouts, but instead of the large size qualifier, use sw600dp to indicate the two-pane layout is for screens on which the smallest-width is 600 dp:

When inflating a layout, if the device is a tablet, then this folder (or layout-sw600dp-land) is searched first, depending on the orientation. If the **tablet layout is portrait**, this layout is searched first, otherwise if the **tablet layout is landscape**, layout-sw600dp-land is searched first. The general layout folder above is searched after, ***only *** if the layout needing inflated is not in any of the sw600dp folders, as the sw600dp folders are more specific, so they are always searched first.

#### layout-sw600dp-land
As `layout-sw600dp`, but the difference is this folder stores landscape layouts and the former stores portrait layouts, for **tablets**.


### Drawable folders
Currently only hosting one drawable folder, but likely in future will also split drawables. This section remains as a placeholder.


## Tracking Modes

### Manual Tracking
The manual tracking mode offered by this application makes use of external offline tracking software. The idea is to record a video, and whilst recording, we can tap on the location of an object. Tapping on an object stores information regarding the x and y coordinates, in a YML file. We can make use of this data file when offline tracking, in order to track accurately. This is known as manual correction.

### Automatic Tracking
The application also offers automatic tracking via template matching. Rather than using offline tracking software, we can select a template on an android device, and use openCV functions to search for the closest match to this template in each camera frame. We can then draw a bounding box around the closest match and include this annotation in our final video. This is known as online tracking.

The data file is formatted in the following way:

```
framenumber: 90
    timestamp: 00:00:03
    x: 256
    y: 181
framenumber: 180    
    timestamp: 00:00:06
    x: 280 
    y: 193
...
...
...

```

## Automatic Tracking Methods
Still to discuss with Ben, but ideally would like to implement matchTemplate and at least one other method such as CamShift or SURF descriptors with FLANN matching.
An interesting idea is implementing FLANN matching but using both SURF and SIFT descriptors, and analysing which descriptor is faster (SURF is claimed to be faster).



## Dissertation ideas
1. Technical evaluation of the test devices (S6 and Google Nexus 5X)<br />
  a) Camera/CPU specs, fps, resolution, colour space<br />
2. Recording/tracking prototype description (for manual and automatic tracking?)<br />
  a) Matching methods for matchTemplate (e.g SQDIFF, CCOEFF, etc)<br />
  b) Talk about SURF vs SIFT dsscriptors if I use Features2D for online tracking<br />
3. Descriptions and evaluations of the different automatic tracking methods<br />
  a) Evaluate based on efficiency, reliability and simplicity<br />
  b) If using Features2D framework, can compare SURF vs SIFT descriptors (SURF claimed to be faster, is this claim true?)<br />
  c) Suggestions for optimisation (e.g. downscaling image, searching only part of image, etc)<br />
  d) Talk about each tracking method in detail, how it works, its advantages and disadvantages<br />
4. Evaluation of the overall program<br />
  a) Usability, are android devices suitable?<br />
  b) Advantages and disadvantages to current system<br />
  c) Is it a practical application?<br />
   
   
   
### Sources
- OpenCV4android Docs: <http://opencv.org/platforms/android.html> 
- Writeup on different possible tracking methods (also includes sensor information): https://docs.google.com/document/d/1jP9_py3FzA-sxTt6PLTENPkShpYYiEQyr_QhVkRh49U/edit?usp=sharing



    
    










