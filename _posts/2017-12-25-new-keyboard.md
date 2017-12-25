---
id: 245
title: New Keyboard
date: 2017-12-25
author: Jorden
layout: post
guid: http://jordenlowe.com/?p=246
permalink: /2017-12-25-new-keyboard
categories:
  - c
  - general
tags:
  - c
  - keyboard
  - qmk
---
Built another keyboard recently called Nyquist.  You can check out the website here: [keeb.io](https://keeb.io/collections/split-keyboard-parts/products/nyquist-keyboard?variant=48309345990).  The neato thing about these custom keyboards is that you can create your own layout for the keys.  Say if you want to have F10, 11 and 12 on this tiny keyboard because you debug code, then you are free to add them.  In fact, you can add them anywhere and these boards are used in video games for macros to programming and anything else you can bind to a button.

Anyways, I have some code that runs these keyboards here: [My fork of QMK](https://github.com/supermitsuba/qmk_firmware).  This code, while took a while to read, is pretty manageable and I was able to create custom animations pretty easily.  I have 3 keyboards I use:

1. (Let's split)[https://github.com/supermitsuba/qmk_firmware/tree/master/keyboards/lets_split]
2. (Nyquist)[https://github.com/supermitsuba/qmk_firmware/tree/master/keyboards/nyquist]
3. (xd75)[https://github.com/supermitsuba/qmk_firmware/tree/master/keyboards/xd75]

Each of them have the same animations and base functionality, so I don't have to recreate the wheel each time.  Just have to set up the keys I want and upload the firmware.  Fun times to be able to hack on your keyboard, too.

![My keyboard](/wp-content/uploads/2017/IMG_0239.png)