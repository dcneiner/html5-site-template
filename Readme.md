# Blank HTML5 Website Framework

The whole point of this is to abstract things I do over and over again when starting a new web design/development project. This reflects my workflow and may change over time because of that. 

## Included Resources

It includes a few additional items by default:

* [HTML5 Reset Stylesheet](http://html5doctor.com/html-5-reset-stylesheet/) by [Richard Clark](http://richclarkdesign.com/) -- *which was adapated from the Eric Myer's Reset CSS file.*
* [Modernizr](http://modernizr.com) -- Which takes care of adding the HTML5 shim for IE in addition to providing a fantastic way to provide progressive enhancment for new features whose support is still spotty. 
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

I use a convention in this template that starts the page load with a `no-js` class attached to `html`. The first `script` tag, however, does a replace, and changes `js` to `no-js`. You can save a few lines by just assiging the class vs. doing a replace, but I often add additional classes to the `html` class. In your CSS file, you can hide JS specific elements from non-JS enabled browsers or hide elements from browsers with JS enabled. By running this in the `head`, it changes up the page before it even renders, avoiding an awkward Flash of Unstyled Content (FOUS):

    .no-js .collapsed { display: block; } /* Be sure blocks are hidden if JS is disabled */
    .js    .collapsed { display: none;  } /* With JS enabled, hide these blocks. They will be shown via JS */