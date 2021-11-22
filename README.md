# Sass MediaScreen

[![Version](https://img.shields.io/npm/v/sass-mediascreen.svg)](http://npm.im/sass-mediascreen)
[![Downloads](https://img.shields.io/npm/dm/sass-mediascreen.svg)](http://npm.im/sass-mediascreen)

Mixins for checking **group of devices** (mobile, tablet, laptop, desktop) or **device by name** (iPhone 5, iPhone X, iPhone 11 Pro Max, iPad Pro 12.9, etc). Expandable and very simple for usage.


### Helpful Links

- [Demo](http://mediascreen.gvozdb.ru)


### Important

> Don't check the adaptability in the browser DevTools, there are [incorrectly calculated dimensions](https://codepen.io/gvozdb/pen/bPQmvv) of the sides in the landscape orientation of the device.
> It is better to check on a real device or in a simulator (for example, xCode Simulator).

> Use [group-css-media-queries](https://github.com/Se7enSky/group-css-media-queries) to optimize media queries. Without it, a lot of the same `@media ...` code is generated, especially if for the sake of convenience to use the mixin `@include device()` in each selector separately. Wrapper for Gulp - [gulp-group-css-media-queries](https://github.com/avaly/gulp-group-css-media-queries).


## Table of Contents

- [Installation](#installation)
- [Documentation](#documentation)
    - [Examples](#examples)
    - [List of supported devices](#list-of-supported-devices)
    - [Expanding the list of devices](#expanding-the-list-of-devices)
- [Credits](#credits)
- [License](#license)


## Installation

```bash
$ yarn add sass-mediascreen
or
$ npm install sass-mediascreen
or
$ curl -O https://raw.githubusercontent.com/gvozdb/sass-mediascreen/master/_mediascreen.scss
```


## Documentation

Include mixins to app:

```scss
@import "mediascreen";
```


### Examples:

It can be used like this:

```scss
@include device(iPhone5, portrait) {
    // portrait orientation
    // iPhone 5, iPhone 5s, iPhone 5c, iPhone SE
}
@include device(iPhone6Plus iPhoneXR, landscape) {
    // landscape orientation
    // iPhone 6+, iPhone 6s+, iPhone 7+, iPhone 8+, iPhone XR, iPhone 11
}
@include device(iPadPro10 iPadPro11 iPadPro12) {
    // all orientations
    // iPad Pro 10.5, iPad Pro 11, iPad Pro 12.9
}
```

Or like this:

```scss
@include device(desktop) {
    // all orientations
    // desktop
}
@include device(mobile tablet laptop, landscape) {
    // landscape orientation
    // mobile, tablet, laptop
}
```

Or even like this:

```scss
@include device(mobile-landscape tablet laptop) {
    // landscape orientation
    // mobile

    // all orientations
    // tablet, laptop
}
@include device(mobile-landscape tablet laptop, portrait) {
    // landscape orientation
    // mobile

    // portrait orientation
    // tablet, laptop
}
```

There are also common mixins:

```scss
@include screen(min-width, max-width, orientation) {/*...*/}
@include min-screen(width) {/*...*/}
@include max-screen(width) {/*...*/}

@include screen-height(min-height, max-height, orientation) {/*...*/}
@include min-screen-height(height) {/*...*/}
@include max-screen-height(height) {/*...*/}

@include landscape() {/*...*/}
@include portrait() {/*...*/}
```


### List of supported devices:

#### Groups

- Mobiles 320-767px `mobile` `mobile-portrait` `mobile-landscape`
- Tablets 768-1023px `tablet` `tablet-portrait` `tablet-landscape`
- Laptops 1024-1199px `laptop` `laptop-portrait` `laptop-landscape`
- Desktop >=1200px `desktop` `desktop-portrait` `desktop-landscape`

#### Phones

- iPhone 5, 5s, 5c, SE `iphone5` `iphone5s` `iphone5c` `iphonese`
- iPhone 6, 6s, 7, 8 `iphone6` `iphone6s` `iphone7` `iphone8`
- iPhone 6+, 6s+, 7+, 8+ `iphone6plus` `iphone6splus` `iphone7plus` `iphone8plus`
- iPhone X, XS, 11 Pro `iphonex` `iphonexs` `iphone11pro`
- iPhone XR, 11 `iphonexr` `iphone11`
- iPhone XS Max, 11 Pro Max `iphonexsmax` `iphone11promax`
- iPhone 12, 12 Pro, 13, 13 Pro `iphone12` `iphone12pro` `iphone13` `iphone13pro`
- iPhone 12 mini, 13 mini `iphone12mini` `iphone13mini`
- iPhone 12 Pro Max, 13 Pro Max `iphone12promax` `iphone13promax`

#### Tablets

- iPad 1, 2, Mini, Air `ipad1` `ipad2` `ipadmini` `ipadair`
- iPad 3, 4, Pro 9.7" `ipad3` `ipad4` `ipadpro9`
- iPad Pro 10.5" `ipadpro10`
- iPad Pro 11.0" `ipadpro11`

#### Laptops

- iPad Pro 12.9" `ipadpro12`

_Well, Yes. iPad Pro 12.9" is a laptop because of its size._

---

### Expanding the list of devices:

You can add support for custom devices or group of devices without editing the source.
Before `@import "mediascreen"`, you must specify `$ms-devices` variable with a list of additional devices:

```scss
$ms-devices: (
    desktop-sm: (
        group: true, // group of devices
        min: 1200px,
        max: 1919px,
    ),
    desktop-md: (
        group: true, // group of devices
        min: 1920px,
        max: 2879px,
    ),
    desktop-lg: (
        group: true, // group of devices
        min: 2880px,
    ),
    pixel2xl: (
        group: false, // specific device
        width: 411px, // or 412px?..
        height: 823px,
        pixel-ratio: 3.5,
    ),
    macbook12: (
        group: false, // specific device
        orientation: landscape,
        width: 1440px,
        height: 900px,
        pixel-ratio: 2,
    ),
    imac27: (
        group: false, // specific device
        orientation: landscape,
        width: 5120px,
        height: 2880px,
    ),
);
```


## Credits
- [Pavel Gvozdb](https://gvozdb.ru)

## License
This software is open-source licensed under the [MIT license](https://opensource.org/licenses/MIT).
