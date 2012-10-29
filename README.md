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

$ git clone git@github.com:bananos/aperture-web-export.git
$ cd aperture-web-export
$ sudo cp -R export-theme /Applications/Aperture.app/Contents/Resources/WebThemes/
$ sudo chown -R root:wheel /Applications/Aperture.app/Contents/Resources/WebThemes/export-theme

```
Once you've copied new theme to Aperture folder it should be available in the list of possible themes for Web Journal:

![Aperture Web Journal](http://bananos.github.com/aperture-web-export/resources/aperture-export.png)

### Step 2. Install requirements.txt for python

Use ``pip`` to install python dependencies:
```bash
$ pip install -r requirements.txt
```
or ``easy_install`` if you don't have pip yet:
```bash
$ while read line; do sudo easy_install $line; done < requirements.txt
```


Usage
------
In order to quickly play with script, there's a sample Aperture Web Journal in repo:

```bash
$ chmod +x parser.py
$ ./parser.py --path=sample-web-journal > journal.json

```

Here's a prettified JSON output:
```json
{
    "img1": {
        "src": "/Users/bananos/Projects/aperture-web-export/sample-web-journal/thumbnails/thumb-1.jpg",
        "latitude": "50.4355",
        "altitude": "173",
        "longitude": "30.562833",
        "height": "672",
        "width": "900",
        "shutter speed": "1/15",
        "date": "6/10/12 6:44:30 PM GMT+03:00",
        "alt": "",
        "caption": "Second caption",
        "aperture": "2.8"
    },
    "p1": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat.",
    "img2": {
        "src": "/Users/bananos/Projects/aperture-web-export/sample-web-journal/thumbnails/thumb-2.jpg",
        "date": "6/10/12 7:05:37 PM GMT+03:00",
        "altitude": "166",
        "longitude": "30.552667",
        "height": "900",
        "width": "672",
        "shutter speed": "1/30",
        "latitude": "50.434167",
        "alt": "",
        "aperture": "2.8"
    },
    "p2": "Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat volutpat.",
    "img3": {
        "src": "/Users/bananos/Projects/aperture-web-export/sample-web-journal/thumbnails/thumb-3.jpg",
        "latitude": "50.4355",
        "altitude": "173",
        "longitude": "30.561",
        "height": "900",
        "width": "672",
        "shutter speed": "1/17",
        "keywords": [
            "arsenale",
            "test"
        ],
        "date": "6/10/12 6:28:02 PM GMT+03:00",
        "alt": "",
        "caption": "My caption",
        "aperture": "2.8"
    }
}

```


