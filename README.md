# Viewhance #

A browser extension to enhance the browser's default media viewer.

To try it out (when installed), open a media file ([image](https://upload.wikimedia.org/wikipedia/commons/e/ec/StLouisArchMultExpToneMapped.jpg) / [video](https://upload.wikimedia.org/wikipedia/commons/d/de/Hdr_time_lapse_montage.ogv) / [audio](https://upload.wikimedia.org/wikipedia/en/3/3d/Sample_of_Daft_Punk's_Da_Funk.ogg)) in a new tab.

[Changelog / FAQ](https://tiny.cc/Viewhance)

## Features ##
- Default sizing modes and switching between them via shortcuts or with mouse clicks
- Custom CSS (background color for the page or media, hidden scrollbars...)
- Custom information about the media in the tab title
- Floating menu (mouse cursor over the top-left)
- Mouse wheel zooming (off by default)
- Centering content (default)
- Rotate/Flip (via shortcuts or from the menu)
- Sending the address of the media to different services (such as reverse image search)
- Frame extraction for animated images (GIF, APNG, WEBP)
- Handling SVG and data:URIs
- Forced inlining (show media instead of download)
- Native DASH, HLS, MSS streaming (if the browser can support it)
- Customizable media attributes (autoplay, loop, controls, mute, volume)
- Opening images from regular web-pages with right long-press or with shortcut (off by default)

## Browser/platform support ##
The following platforms are supported, for each the latest browser version:

- **crx** - many Chromium based [browsers](https://en.wikipedia.org/wiki/Chromium_\(web_browser\)#Browsers_based_on_Chromium) ([Chrome](https://chrome.google.com/webstore/detail/impppjchnpfgknmbaaghfeopcgfoilac), Opera 15+, Vivaldi, Edge...), or browsers with WebExtension support (e.g., [Firefox](https://addons.mozilla.org/addon/viewhance/))
- **xpi** - XUL based platforms (older Firefox, SeaMonkey, Pale Moon...)
- **oex** - Opera 12 (Presto based)
- **mxaddon** - Maxthon
- **safariextz** (legacy) - Safari v5.1 - v12

## Build ##
```
./build.py [platform(s)] [-meta] [-min] [-pack] [-all] [-version=x.x.x]
```

All arguments are optional. The output and temporary files go into the `build` directory.
Without arguments the script will generate the necessary files for each non-disabled platform.
Additional information for specific platforms can be found in their directories.

`platf1 platf2...` - list of platforms (directory names under `platform/`) if building for all platforms is not desired

`-meta` - generate only meta-data (localization, manifest files)

`-pack` - creates installable/distributable packages (with `-meta` it will also generate meta files for updating)

`-min` - compress source files (JS, HTML, CSS) (Java is required)

`-all` - build disabled platforms as well (if it's not listed as a platform already)

`-version=x.x.x` - use custom version number, instead of an auto-generated based on the current date-time (YYYY.MMDD.HHII)

Examples:
```
# Prepare directories for non-disabled platforms
./build.py

# Prepare directories for Firefox (XUL) and Opera (Presto)
./build.py xpi oex

# Prepare directories and package them for every platform (including disabled)
./build.py -pack -all

# Prepare, minify, and package for Chromium
./build.py crx -min -pack

# Generate meta-data for Maxthon and Safari
./build.py -meta mxaddon safariextz
```

## Contribution ##
- **Localization** You can use [this helper tool](https://deathamns.github.io/Viewhance/localizer.html) for translating strings. The result can be sent as a pull request on GitHub (instructions are shown when you export your work on the localizer page).
- **Code** If you have a bug-fix, or did some tweaks, then you can send a pull request with your changes. Criteria: Try to respect the code styling, use [`eslint`](http://eslint.org/), don't diverge too much from the main goal; viewing enhancements.
The code must work on all supported platforms, except if the browser's extension API doesn't provide appropriate functionality, then fail silently.
