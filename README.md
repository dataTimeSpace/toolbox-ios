# <img src="/README-resources/DTSLogoAdaptive.svg" width="32" height="32"> Data Time Space Toolbox

## Read First

The Toolbox and Edge Server make up a shared research platform
for exploring spatial computing as a community. This research platform is not an out of the box
production-ready enterprise solution. Please read the [MPL 2.0 license](LICENSE) before use.

## Installation
How to build and run Data Time Space Toolbox iOS App from your Mac OS computer from source code

1. Clone the toolbox-ios repo from GitHub.

```
git clone https://github.com/dataTimeSpace/toolbox-ios.git
```

2. Initialize the git submodules to get the correct versions of the edge-server
   and userinterface repositories.

```
cd toolbox-ios
git submodule init
git submodule update
```

3. Install some additional dependencies using
   [CocoaPods](https://guides.cocoapods.org/using/getting-started.html). If you don't already have
    CocoaPods installed you should first run `sudo gem install cocoapods`, otherwise `pod install`
    will fail.

```
pod install
```

4. Navigate to the vuforia-spatial-edge-server submodule and run the same commands here to initialize
   its own submodule (vuforia-spatial-core-addon).

```
cd bin/data/vuforia-spatial-edge-server
git submodule init
git submodule update
```

5. Run `npm install` twice: once in vuforia-spatial-edge-server and again in its
   addons/vuforia-spatial-core-addon to install all of its dependencies.

```
npm install
cd addons/vuforia-spatial-core-addon
npm install
```

6. Download the latest Vuforia SDK for iOS from https://developer.vuforia.com/downloads/sdk
   (Click the "Download for iOS" link for *vuforia-sdk-ios-\[version-number\].zip*).

   This project was last updated with Vuforia SDK version: `9.6.4`

 - Paste the Vuforia.framework file from the `build` directory of the download into the top level
   of the `toolbox-ios` directory.
 - If the latest Vuforia SDK version has been updated beyond this documentation and you have trouble
   compiling the app, please file an issue.

7. Get a Vuforia Engine license key from http://developer.vuforia.com by logging in and navigating
   to `Develop > License Manager > Get Development Key`. The name of your key doesn't matter.

   Create a new file in the `vuforia-spatial-toolbox-ios/Vuforia Spatial Toolbox` directory named
   `vuforiaKey.h` and copy-and-paste the following contents into it. Replace the `vuforiaKey` const
   with your key (a very long, generated sequence of characters):

```
//  vuforiaKey.h
//  Licensed from http://developer.vuforia.com

#ifndef vuforiaKey_h
#define vuforiaKey_h

const char* vuforiaKey = "Replace this string with your license key";

#endif /* vuforiaKey_h */
```

8. When these files are in place, open Vuforia Spatial Toolbox.**xcworkspace**. Make sure to
   open the .xcworkspace and not the .xcodeproj, otherwise the dependencies won't load. Make sure
   Xcode is set up with your Apple developer profile for code signing (in Xcode, click on the Vufora Spatial Toolbox
   project file to view its properties, click on Vuforia Spatial Toolbox under "Targets", and go to the "Signing
   & Capabilities" tab. You will need to add an Apple Developer account to Xcode to proceed. When all is set up, you
   should be able to compile and run the project on your iOS device (it won't run on the simulator; you need to have an
   iOS device connected).

### Device Compatibility

While this codebase is fundamentally compatible with iPhones and iPads, it has currently only
been recently tested with iPhones. This has been developed primarily with iOS 12, 13, and 14
and with device models iPhone 6S through 11 Pro.

### Additional Documentation

Please refer to our [documentation repository](https://github.com/dataTimeSpace/vuforia-spatial-toolbox-documentation)
for additional tutorials, setup guides, and introductions to various aspects of the system.

### Notes

If your log window is being spammed with `[Process] kill() returned unexpected
error 1` check out [this StackOverflow answer](https://stackoverflow.com/a/58774271).
