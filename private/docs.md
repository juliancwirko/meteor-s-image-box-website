## Simple image popup/lightbox for Meteor

### Usage

Add package:

    meteor add juliancwirko:s-image-box

Then you can use two functions:

#### sImageBox.open()

```javascript
sImageBox.open('/path/to/full/image', {
    originalHeight: false, // image will be responsive you can enable original height
    originalWidth: false, // image will be responsive you can enable original width
    animation: '' //image entry animation (scale, fadeIn, zoomIn, slideInDown)
});
```

#### sImageBox.close()

```javascript
sImageBox.close()
```

### Usage example in your app

Html:

```html
<template name="categoryPageItemImage">
    <div class="image-preview">
        <div class="js-activate-s-image-box" data-full-image-src="{{fullUrl}}" style="background-image: url({{previewUrl}})"></div>
    </div>
</template>
```

JavaScript:

```javascript
Template.categoryPageItem.events({
    'click .js-activate-s-image-box': function (e) {
        var imgPath = $(e.currentTarget).data('full-image-src');
        if (imgPath) {
            sImageBox.open(imgPath);
        }
    }
});
```

or you can pass more custom settings for this one:

```javascript
Template.categoryPageItem.events({
    'click .js-activate-s-image-box': function (e) {
        var imgPath = $(e.currentTarget).data('full-image-src');
        if (imgPath) {
            sImageBox.open(imgPath, {
                originalHeight: true,
                originalWidth: true,
                animation: 'slideInDown'
            });
        }
    }
});
```

### sImageBox global config

You can set up your global config and also you will be able to overwrite it with custom `sImageBox.open()` calls. If you need your global config place the code below in the client side of your app:

```javascript
Meteor.startup(function () {

    sImageBox.config({
        originalHeight: false, // image will be responsive you can enable original height
        originalWidth: false, // image will be responsive you can enable original width
        animation: '' //image entry animation (scale, fadeIn, zoomIn, slideInDown)
    });

});
```

### Styling and custom animations

You can of course overwrite the styles of sImageBox. Go to GitHub repo and check `s-image-box.css` file. You will find all styles there.

If you want to write your own animation for the image you should add it in you css files. Remember to name it like: `.s-image-box-anim-yourAnimationName` then pass `yourAnimationName` in the config. See `s-image-box.css` for examples.

### Changelog

- v0.1.1 Settings extend fix
- v0.1.0 Init. Standard simple image popup.

Ideas and PRs are welcomed.

### License

MIT

### Download and use this website for your documentation

```
$ git clone https://github.com/juliancwirko/meteor-s-image-box-website.git
$ cd meteor-s-image-box-website
$ rm -rf .git
$ meteor
```
[https://github.com/juliancwirko/meteor-s-image-box-website.git](https://github.com/juliancwirko/meteor-s-image-box-website.git)

### Check out other tools for Meteor:

* [Prettify and export your raw git diff output](https://atmospherejs.com/juliancwirko/pretty-diff)
* [Foundation 5 with Scss for Meteor](https://atmospherejs.com/juliancwirko/zf5)
* [Stylus, Flexbox grid system](https://atmospherejs.com/juliancwirko/s-grid)
* [Stylus with Jeet, Autoprefixer, Rupture and Nib for Meteor](https://atmospherejs.com/juliancwirko/s-jeet)
* [Notifications for Meteor](http://s-alert.meteor.com)
* [Scotty - Meteor boilerplate](https://github.com/juliancwirko/scotty)
* [Meteor CylonJS wrapper for Arduino board](https://atmospherejs.com/juliancwirko/caprica)
* [Simple accounts system](https://github.com/juliancwirko/meteor-s-id)

### Also check out standalone front-end tools:

* [S-Grid (Stylus, Flexbox grid) GruntJS project scaffold](https://github.com/juliancwirko/s-grid-grunt)
* [Yeoman generator for Zurb Foundation 5](https://github.com/juliancwirko/generator-zf5)
* [Free, very simple and clean starter theme for your Ghost blog](https://github.com/juliancwirko/abc)
* [HTML only and GruntJS based project scaffold](https://github.com/juliancwirko/html-project)