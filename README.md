Aperture web export
====================
Export meta-data in JSON from Aperture Web Journals.


Purpose & original idea
------------------------
[Apple Aperture](http://www.apple.com/aperture/) is a pretty powerful piece of software, which perfectly met my requirements for keeping track 
large amounts of photos. It's also good at advanced image processing and has some additional features like
photobooks creation, web journals/pages, etc. 

The original idea was to be able to write posts for my photo-blog right inside Aperture using its built-in functionality 
for creating webjournals. However, I'm not satisfied with the final result -- none of default web themes fits my custom blog design.
Therefore, I decided to create a simple tool to extract metadata out of Aperture Web Journal into general-purpose JSON to 
be able to use it elsewhere.


Installation
-------------

### Step 1. Install additional Aperture Web Journal theme

We're assuming that your copy of Aperture is located at ``/Applications/Aperture.app/``:
```bash

[bananos@amber]$ git clone git@github.com:bananos/aperture-web-export.git
[bananos@amber]$ cd aperture-web-export
[bananos@amber]$ sudo cp -R export-theme /Applications/Aperture.app/Contents/Resources/WebThemes/
[bananos@amber]$ sudo chown -R root:wheel /Applications/Aperture.app/Contents/Resources/WebThemes/export-theme

```
Once you've copied new theme to Aperture folder it should be available in the list of possible themes for Web Journal:

TODO: screenshot


### Step 2. Install requirements.txt for python

Use pip to install python dependencies:
```bash
[bananos@amber]$ pip install -r requirements.txt
```
or easy_install if you don't have pip yet:
```bash
[bananos@amber]$ while read line; do sudo easy_install $line; done < requirements.txt
```


Usage
------
In order to quickly play with script, there's a sample Aperture Web Journal in repo:

```bash
[bananos@amber]$ chmod +x parser.py
[bananos@amber]$ ./parser.py --path=sample-web-journal > journal.json

```

Here's a prettified JSON output:
```json

{
    "img1": {
        "src": "/Users/bananos/Projects/aperture-web-export/sample-web-journal/thumbnails/thumb-1.jpg",
        "direction": "88.637634",
        "width": "1000",
        "altitude": "173",
        "longitude": "30.565333",
        "height": "746",
        "caption": "IMG_0711",
        "keywords": null,
        "alt": "",
        "latitude": "50.435667"
    },
    "p1": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat.",
    "p2": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat.",
    "img2": {
        "src": "/Users/bananos/Projects/aperture-web-export/sample-web-journal/thumbnails/thumb-2.jpg",
        "direction": "266.124847",
        "width": "1000",
        "altitude": "173",
        "longitude": "30.562833",
        "height": "746",
        "caption": "IMG_0721",
        "keywords": null,
        "alt": "",
        "latitude": "50.4355"
    },
    "img3": {
        "src": "/Users/bananos/Projects/aperture-web-export/sample-web-journal/thumbnails/thumb-3.jpg",
        "direction": "330.919464",
        "width": "1000",
        "altitude": "182",
        "longitude": "30.553167",
        "height": "746",
        "caption": "IMG_0734",
        "keywords": null,
        "alt": "",
        "latitude": "50.435"
    },
    "p3": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat.",
    "p4": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat.",
    "img4": {
        "src": "/Users/bananos/Projects/aperture-web-export/sample-web-journal/thumbnails/thumb-4.jpg",
        "direction": "174.497879",
        "width": "1000",
        "altitude": "173",
        "longitude": "30.561",
        "height": "1338",
        "caption": "IMG_0716",
        "keywords": null,
        "alt": "",
        "latitude": "50.4355"
    }
}

```


