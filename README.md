# InBrain Surveys
[Legacy] Survey library to monetize your mobile app, provided by inBrain.ai

## Requirements
This SDK is targeted to the following tools:
- XCode 10.1 with the Legacy Build System
- Swift 3
- React Native 0.59.1

If you are using newer versions of these tools, please refer to the 'inbrain-surveys' npm package.

## Installation

Install and link the module:

`$ npm install inbrain-surveys-legacy --save`

`$ react-native link inbrain-surveys-legacy`

### Extra steps iOS

Visit your app’s ***Target*** in the Project Settings and Choose the ***General*** tab.
Scroll down until you hit the ***Embedded Binaries*** section… 
1) Press ‘+’, Add Other...
2) Select the **InBrainSurveys_SDK_Legacy.framework** in your project `nodes_modules/inbrain-surveys-legacy/ios/Frameworks` folder
4) Search for `Framework Search Paths` in your Target and add a recursive entry `$(SRCROOT)/../node_modules/inbrain-surveys-legacy`
3) Confirm

Configure your info.plist as specified [here](https://github.com/inBrainSurveys/InBrainSurveys_SDK_Swift/blob/master/README.md#configuration)

### Extra steps Android
Add jitpack repository you your gradle configuration (`android/build.gradle`)
```
allprojects {
    repositories {
        ...
        maven { url "https://jitpack.io" }
        ...
```


## Usage
```javascript
import inbrain from 'inbrain-surveys-legacy';
```
Available functions:
### Initialise the SDK
```javascript
inbrain.init(clientId: string, secretId: string)
```
* clientId: The client ID obtained from your account manager (NOT USED ON iOS, use info.plist instead)
* clientSecret: The client secret obtained from your account manager.

### Set the app user identifier
```javascript
inbrain.setAppUserId(userId: string)
```
* clientId The user identifier (usually an email)

### Show the surveys webview
```javascript
inbrain.showSurveys()
```

### Get the rewards
```javascript
inbrain.getRewards() (Useful for server less app)
```

### Confirm a list of rewards
```javascript
inbrain.confirmRewards(rewards: InBrainReward[]) (Useful for server less app)
```
* rewards: List of rewards to confirm

### On webview dismissed
```javascript
inbrain.setOnCloseListener(callback: () => void) 
```
* callback: callback to perform when it happens

### Only supported on iOS
### Set the webview title
```javascript
inbrain.setTitle(title: string)
```
* title: The title to display

### Set the webview navbar color
```javascript
inbrain.setNavbarColor(color: string)
```
* color: hexadecimal string color (e.g #ff0000)

### Set the webview button color
```javascript
inbrain.setButtonColor(color: string)
```
* color: hexadecimal string color (e.g #ff0000)

## Development
To install and build locally, pull the repository.
Run 
```
npm install 
npm run build 
npm run start 
```

You can alternatively run 'npm run watch' instead of 'npm run build' if you want live reload.

## Troubleshoots
### [BUILD TIME] 'InBrainSurveys_SDK_Legacy/InBrainSurveys_SDK_Legacy-Swift.h' file not found
This problem usually happens if the framework is not set in the Embedded Binaries. See above for set up.
Clean and build the project after changes.

### [BUILD TIME] framework not found InBrainSurveys_SDK_Legacy
This problem usually happens if the 'Framework Search Path' is not set correctly. See above for set up.
Clean and build the project after changes.

### [RUNTIME] Library not loaded: @rpath/libswiftCore.dylib
This problem can happen if your project doesn't have the Swift standard libraries included. Set the 'Always Embed Swift Standard Libraries' to yes in your target to fix it.
Clean and build the project after changes.

### [RUNTIME] Application crashing without obvious reasons
This problem can happen if you didn't configure the info.plist correctly. See above for set up.
Clean and build the project after changes.

