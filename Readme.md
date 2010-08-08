# Blank HTML5 Website Framework

The whole point of this is to abstract things I do over and over again when starting a new web design/development project. This reflects my workflow and may change over time because of that. 

## Production Recommendations

During development I work with multiple CSS files as needed, and multiple JS files for each part of the site or functionality. But when I move to production, I normally put together a build setup that optimizes the code for production.

You should have a build process that combines and minifies the CSS files, and combines and minifies your JS files as well. Remember Modernizr includes the HTML5 shim so you need to keep that in the `head`, but your production ready combined JS should be placed just before the closing `</body>` tag. 

I personally use [YUICompressor](http://developer.yahoo.com/yui/compressor/) for CSS and [Google Closure Compiler](http://code.google.com/closure/compiler/) for JS.

## Included Resources

It includes a few additional items by default:

* [HTML5 Reset Stylesheet](http://html5doctor.com/html-5-reset-stylesheet/) by [Richard Clark](http://richclarkdesign.com/) -- *which was adapted from the Eric Myer's Reset CSS file.*
* [Modernizr](http://modernizr.com) -- Which takes care of adding the HTML5 shim for IE in addition to providing a fantastic way to provide progressive enhancement for new features whose support is still spotty. 
* [jQuery](http://jquery.com) -- A local copy is included for development, then for production simply un-comment the Google CDN link and remove the local `<script>` tag.
  
## File Layout

    index.html
    Readme.md                     
    css/  
      - layout.css                // empty, just imports reset.css
      - reset.css
    fonts/                        // empty, for storing web fonts
    images/                       // empty, for all site images
    js/
      - site.js                   // I almost always need at least one script file, this gets me started
      - lib/                      // External libraries and plugins should go here
          - jquery-1.4.2.min.js
          - modernizr-1.5.min.js

## Using `.js` and `.no-js` helper classes

I use a convention in this template that starts the page load with a `no-js` class attached to `html`. *(Update: Normally I have a snippet of code that does the swap from `no-js` to `js`, but thankfully Modernizr does this automatically if `no-js` exists!)* In your CSS file, you can hide JS specific elements from non-JS enabled browsers or hide elements from browsers with JS enabled. By running this in the `head`, it changes up the page before it even renders, avoiding an awkward Flash of Unstyled Content (FOUS):

    .no-js .collapsed { display: block; } /* Be sure blocks are hidden if JS is disabled */
    .js    .collapsed { display: none;  } /* With JS enabled, hide these blocks. They will be shown via JS */
    

## Optional Helper Shell Script

The `site` file is a helper script that will take care of setting up a new directory for you to start working on your new site. This script will first create the directory then export all the needed files (without the `.git` directory or any `.git*` files) to the new directory. This is the preferred method of utilizing this template framework.

You can use the `site` command via the command line, like this:

    ./site /path/to/new/site

You may need to mark this script as executable before using it:

    chmod +x site

Finally, you can move this file to /usr/bin to use the `site` command from any directory. If you do this, be sure to uncomment the `cd ~/Development...` line and update the path to the location of this git repository on your local computer.