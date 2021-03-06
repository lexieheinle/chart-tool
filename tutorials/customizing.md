# Customizing your Chart Tool

The `/custom` folder contains a series of files that allow you to customize your Chart Tool as you find appropriate. If you want to add to the core Chart Tool library's functionality, change the styling of charts or tweak your Meteor configuration, this is where you'll do it.


----------


### `chart-tool-config.json`

The main configuration file. Chart Tool uses this file to scaffold a basic chart object, set parameters throughout the library, and so on. Includes instructions for the Chart Tool on how to abbreviate months, debounce and tooltip timeouts, desktop and mobile ratios, style prefixes, and so on. See [this example file](https://github.com/globeandmail/chart-tool/blob/master/tutorials/chart-tool-config-sample.json) for an explanation of what each configuration parameter does.

If you're looking to use S3 to host chart thumbnails, check out [the tutorial](https://github.com/globeandmail/chart-tool/blob/master/tutorials/thumbnails.md).


### `meteor-config.js`

Configuration file for the interface. Defines the schema for a chart within the database (`app_settings.chart`), points to an [animal names API](https://github.com/globeandmail/chart-tool/blob/master/tutorials/interface.md#collaborative-editing), and sets print configurations throughout the app. 


### `custom.js`

A function that is optionally invoked for each chart after all of a chart's elements are rendered. Useful to perform blanket tweaks to a chart's structure as mandated by a style guide — for instance, if your style requires axis labels, you can easily add them via `custom.js` by invoking the axis nodes and dimensions and generating new SVG `text` objects. Off by default. If you'd like to enable the use of `custom.js`, make sure to change the `CUSTOM` declaration in `chart-tool-config.json` to `true`.


### `base.scss`

This base file can contain overrides for fonts, sizes, and other SCSS variables Chart Tool needs to build a fresh copy of its style library. If you don't want to override any base SCSS variables, just comment this file out.


### `fonts.scss`

Got some custom fonts you want to point to in your `base.scss` file? Put your `@font-face` declarations here.


### `custom.scss`

Similar to `base.scss`, except this file sits at the bottom of Chart Tool's style imports file, meaning any styles in this file will override any other styles previously set in the library. Like with `base.scss`, if you don't want to add custom styles, just leave the file blank or commented out.

### `meteor-custom.scss`

This file overrides style settings on the Meteor-side of things. Useful for setting your own [print styles](https://github.com/globeandmail/chart-tool/blob/master/tutorials/print.md), adding base64 versions of fonts, and tweaking colours and styles within the interface.

----------


#### Deleting files in the `/custom` folder

Chart Tool expects to be able to see these custom files in the `/custom` folder, even if they're empty. Don't remove them! Bad things could happen if you do.

#### A note on class prefixes

Chart Tool charts are **aggressively** namespaced to prevent CSS collisions when rendering on news websites. If you want to override chart class prefixes (for instance, changing all chart classes from `ct-[chart-element-here]` to `globe-[chart-element-here]`), you'll need to make that change in two places: `chart-tool-config.json`'s `prefix` property, and `base.scss`'s `$prefix` SCSS variable.
