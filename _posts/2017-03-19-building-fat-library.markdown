---
layout: post
title:  "Making a fat libSDL.a for iOS development"
date:   2017-03-19 21:24:00 +1100
categories: sdl iOS 
---

Building the SDL Xcode-iOS project will output for i386 if the simulator target is selected, or ARM for a physical device.
This results in two output libraries named `libSDL2.a`. 

For development it is handy to have a single fat library that supports both platforms.

Enter the macOS `lipo` command. 

Copy each library from the `Debug-iphoneos` and `Debug-iphonesimulator` in the derived data and combine them:

	lipo -create libSDL2arm.a libSDL2i386.a -output libSDL2.a


