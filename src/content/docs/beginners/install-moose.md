---
layout: page
background: '/img/bg-wiki.jpg'
title: 'Install Moose'
---

In this article, we describe how to install Moose.

## Installation

1. Install Pharo Launcher
2. Get Moose Image

### Step 1 - Install Pharo Launcher

The easiest way to install Moose is to use the Pharo Launcher.
You can download it from the [Pharo website.](https://pharo.org/web/download)

### Step 2 - Get Moose Image

From the Pharo Launcher, you can download a Moose image.
It corresponds to a Pharo image (see the [pharo open documentation](https://github.com/pharo-open-documentation)) with the Moose tools installed.

The [ReadMe](https://github.com/moosetechnology/Moose#readme) of the Moose project describes how to get the latest Moose image.
It is usually safe to take the highest version available even if marked 'developement'.

Once the image downloaded, you just need to run it with from the Pharo Launcher.

## Add all GitHub releases in the launcher

If you want to access all versions of Moose, instead of the most recent ones, you can use the GitHub releases. To do so, add this project into the pharo launcher:

- Download the PharoLauncher (see Step 1 of the previous section)
- Open PharoLauncher
- Open a playground (<kbd>Ctrl</kbd> + <kbd>O</kbd>, <kbd>Ctrl</kbd> + <kbd>W</kbd>)
- Execute the following piece of code

```smalltalk
| sources |

sources := {
    "Add Moose"
    PhLTemplateSource new
        type: #HttpListing;
        name: 'Moose';
        url: 'https://github.com/moosetechnology/Moose/releases';
        filterPattern: 'href="([^"]*/(Pharo|Moose)[0-9][^"]*.zip)"';
        templateNameFormat: '{6} ({5})' }.
PhLUserTemplateSources sourcesFile writeStreamDo: [ :s |
    (STON writer on: s)
        newLine: String lf;
        prettyPrint: true;
        nextPut: sources ]
```

- Close the playground
- `New >> Moose >> Your version`

![Download Moose image](res/downloadMooseGitHubReleases.gif)
