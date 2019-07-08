# sass-mediascreen

[![Version](https://img.shields.io/npm/v/sass-mediascreen.svg)](http://npm.im/sass-mediascreen)
[![Downloads](https://img.shields.io/npm/dm/sass-mediascreen.svg)](http://npm.im/sass-mediascreen)

Sass **media queries mixins** for checking **group of devices** (mobile, tablet, laptop, desktop) or **device by name** (iPhone 5, iPhone X, iPad Pro 12.9, etc). Expandable and very simple for usage.

##### [Demo](http://mediascreen.gvozdb.ru)


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
    // iPhone 6+, iPhone 6s+, iPhone 7+, iPhone 8+, iPhone XR
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

##### Groups

- Mobiles `mobile` `mobile-portrait` `mobile-landscape` 320-767px
- Tablets `tablet` `tablet-portrait` `tablet-landscape` 768-1023px
- Laptops `laptop` `laptop-portrait` `laptop-landscape` 1024-1199px
- Desktop `desktop` `desktop-portrait` `desktop-landscape` >=1200px

##### Phones

- iPhone 5, 5s, 5c, SE `iphone5` `iphone5s` `iphone5c` `iphonese`
- iPhone 6, 6s, 7, 8 `iphone6` `iphone6s` `iphone7` `iphone8`
- iPhone 6+, 6s+, 7+, 8+ `iphone6plus` `iphone6splus` `iphone7plus` `iphone8plus`
- iPhone X, XS `iphonex` `iphonexs`
- iPhone XR `iphonexr`
- iPhone XS Max `iphonexsmax`

##### Tablets

- iPad 1, 2, Mini, Air `ipad1` `ipad2` `ipadmini` `ipadair`
- iPad 3, 4, Pro 9.7" `ipad3` `ipad4` `ipadpro9`
- iPad Pro 10.5" `ipadpro10`
- iPad Pro 11.0" `ipadpro11`

##### Laptops

- iPad Pro 12.9" `ipadpro12`

_Well, Yes. iPad Pro 12.9" is a laptop because of its size._


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
    macbook12: (
        group: false, // specific device
        width: 1440px,
        height: 900px,
        pixel-ratio: 2,
    ),
    imac27: (
        group: false, // specific device
        width: 5120px,
        height: 2880px,
    ),
);
```


### Credits
- [Pavel Gvozdb][link-author]

---

### License
This software is open-source licensed under the [MIT license](https://opensource.org/licenses/MIT).

[link-author]: https://github.com/gvozdb
