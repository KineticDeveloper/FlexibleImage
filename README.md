<img alt="FlexibleImage" src="https://github.com/Kawoou/FlexibleImage/raw/master/Preview/Cover.png" style="max-width: 100%">

<center>
![Swift](https://img.shields.io/badge/Swift-3.0-orange.svg)
[![Metal](https://img.shields.io/badge/Apple-Metal-ff00ff.svg)](https://developer.apple.com/metal/)
[![Pod Platform](http://img.shields.io/cocoapods/p/FlexibleImage.svg?style=flat)](http://cocoadocs.org/docsets/FlexibleImage)
[![Pod License](http://img.shields.io/cocoapods/l/FlexibleImage.svg?style=flat)](https://github.com/kawoou/FlexibleImage/blob/master/LICENSE)
<br/>
[![Pod Version](http://img.shields.io/cocoapods/v/FlexibleImage.svg?style=flat)](http://cocoadocs.org/docsets/FlexibleImage)
[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![Build Status](https://travis-ci.org/Kawoou/FlexibleImage.svg?branch=master)](https://travis-ci.org/Kawoou/FlexibleImage)
</center>

A simple way to play with image!

This project can apply effects to images by chaining.


Usage
-----

### Code

![Example Image](https://github.com/Kawoou/FlexibleImage/raw/master/Preview/Example.png)

```swift
import UIKit

import FlexibleImage

/// Generate Example
let image1 = UIImage
    .circle(
        color: UIColor.blue,
        size: CGSize(width: 100, height: 100)
    )?
    .adjust()
    .offset(CGPoint(x: 25, y: 0))
    .margin(UIEdgeInsets(top: 5, left: 5, bottom: 5, right: 5))
    .padding(UIEdgeInsets(top: 15, left: 15, bottom: 15, right: 15))
    .normal(color: UIColor.white)
    .border(color: UIColor.red, lineWidth: 5, radius: 50)
    .image()?
    .adjust()
    .background(color: UIColor.darkGray)
    .image()


/// Effect Example
let image2 = UIImage(named: "macaron.jpg")

let image3 = image2?.adjust()
    .outputSize(CGSize(width: 250, height: 250))
    .exclusion(color: UIColor(red: 0, green: 0, blue: 0.352941176, alpha: 1.0))
    .linearDodge(color: UIColor(red: 0.125490196, green: 0.058823529, blue: 0.192156863, alpha: 1.0))
    .image()

let image4 = image3?.adjust()
    .hardMix(color: UIColor(red: 0.3, green: 0.3, blue: 0.3, alpha: 1.0))
    .image()


/// Mix Example
let image5 = image4?.adjust()
    .append(
        image1!.adjust()
            .outputSize(CGSize(width: 250, height: 250))
            .alpha(0.5)
    )
    .image()

/// Clipping Example
let image6 = image5?.adjust()
    .corner(CornerType(25))
    .image()
```


### Playground

Use CocoaPods command `$ pod try FlexibleImage` to try Playground!


Installation
------------

### [CocoaPods](https://cocoapods.org) (For iOS 8+ projects)

KWDrawerController is available on [CocoaPods](https://github.com/cocoapods/cocoapods). Add the following to your Podfile:

```ruby
pod 'FlexibleImage', '~> 1.5'
```


### [Carthage](https://github.com/Carthage/Carthage) (For iOS 8+ projects)

```
github "kawoou/FlexibleImage" ~> 1.5
```


### Manually

You can either simply drag and drop the `Sources` folder into your existing project.


Supported Features
------------------

FlexibleImage
----------

### Common

| Type | Parameter | Comments |
| ---- | --------- | -------- |
| background() | Color | Background color. |
| opacity() | Float | Change the transparency of the image. |
| alphaProcess() | Bool | Whether to include an alpha value during image processing. |
| ~~blendMode()~~ | ~~CGBlendMode~~ | (Deprecated) ~~Blend mode of the image~~ |
| offset() | CGPoint | The position of the image to be a drawing. |
| rotate() | radius: CGFloat<br/>fixedSize: CGSize [Optional] | Rotate an image. |
| size() | CGSize | The size of the image to be a drawing. |
| outputSize() | CGSize | The size of a Output image. |
| scaling() | CGSize | Scaling the image (ratio) |
| margin() | EdgeInsets | Margin size |
| padding() | EdgeInsets | Padding size |
| corner() | CornerType | To clipping corner radius. |
| border() | color: Color<br/>lineWidth: CGFloat<br/>radius: CGFloat | Drawing a border. |
| image() | | Run the pipeline to create the Output image. |


### Filter

| type | Parameter | Comments |
| ---- | --------- | -------- |
| greyscale() | threshold: Float [Optional] | |
| monochrome() | threshold: Float [Optional] | |
| invert() | | |
| sepia() | | |
| vibrance() | vibrance: Float [Optional] | |
| solarize() | threshold: Float [Optional] | |
| posterize() | colorLevel: Float [Optional] | |
| blur() | blurRadius: Float [Optional] | Not supported by watchOS. |
| brightness() | brightness: Float [Optional] | |
| chromaKey() | color: FIColor<br/>threshold: Float [Optional]<br/>smoothing: Float [Optional] | |
| swizzling() | | |
| contrast() | threshold: Float [Optional] | |
| gamma() | gamma: Float [Optional] | |


### Blend

| type | Parameter |
| ---- | --------- |
| normal() | Color |
| multiply() | Color |
| lighten() | Color |
| darken() | Color |
| average() | Color |
| add() | Color |
| subtract() | Color |
| difference() | Color |
| negative() | Color |
| screen() | Color |
| exclusion() | Color |
| overlay() | Color |
| softLight() | Color |
| hardLight() | Color |
| colorDodge() | Color |
| colorBurn() | Color |
| linearDodge() | Color |
| linearBurn() | Color |
| linearLight() | Color |
| vividLight() | Color |
| pinLight() | Color |
| hardMix() | Color |
| reflect() | Color |
| glow() | Color |
| phoenix() | Color |
| hue() | Color |
| saturation() | Color |
| color() | Color |
| luminosity() | Color |


### Post-processing

| type | Parameter | Comments |
| ---- | --------- | -------- |
| algorithm() | AlgorithmType | Create an image by writing a formula directly on a pixel-by-pixel basis. |
| custom() | ContextType | Add processing directly using Core Graphics. |


### Generate

| type | comments |
| ---- | -------- |
| rect() | Create a rectangular image. |
| circle() | Create a circle image. |
| append() | Combine images to create a single image. |


Changelog
---------

+ 1.0
  - First Release.
+ 1.1
  - Add to clipping corner radius.
+ 1.2
  - Support tvOS, macOS.
+ 1.3
  - Support watchOS.
  - Added monochrome, sepia, vibrance, solarize, posterize filters.
  - Update resize methods.
+ 1.4
  - Add blur filter.
  - Optimize build time.
  - Setup TravisCI
  - Support carthage.
+ 1.5
  - Support Metal depending on the situation.
  - Added brightness, chromaKey, swizzling, contrast, gamma filters.


Requirements
--------------

- iOS 8.0+
- tvOS 9.0+
- macOS 10.10+
- watchOS 2.0+
- Swift 3.0+


License
----------

FlexibleImage is under MIT license. See the LICENSE file for more info.


