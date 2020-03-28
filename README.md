# ReactNativeWithFirebase

Repository describing how to set up a react native app with firebase services


- List of all commands used to create and setup React Native with Firebase services
- This is a work around for those who encounter Pod install errors when using Firebase templates
- More specifically the "use_native_modules!" error.

1) Create a new React Application

  - npx @react-native-community/cli init --template=@react-native-firebase/template NameofApp
  - SOME people will run into the error described above if so follow through the steps given here

2) Navigate to the App directory you made previously

  - cd /NameofApp

3) Install the React Native Firebase App dependencies

  - npm install @react-native-firebase/App

4) Navigate to the ios directory inside your React Native App directory

  - cd ios

5) Using a text editor of choice open the Podfile inside of the ios directory

  - code ./podfile

6) Next add the following to the top of the Podfile after the "target <App Name > do" expression. (you will see similar commands)

  - pod 'RNFBApp', :path => '../node_modules/@react-native-firebase/app'

7) After the previous command enter this similar command

  -  pod 'Firebase/Analytics' // command here 

8) Navigate through the Podfile until you find the line of code: use_native_modules!. Delete or comment it out

  - #use_native_modules! (usually you find this around line 40-50)

9) After you have finished these steps while in thie ./ios directory of your React Native Application run these commands

  - pod install --repo-update
    pod install

10) You may encounter a few errors during this process here are a few that I ran into

  - error: could not find native RNFBApp module did you forget to 'pod install'
  - CocoaPods could not find compatible versions for pod "Firebase/Core"
    // Fix this with pod update Firebase/Core

  - error: React Native CLI uses autolinking for native dependencies, but the following modules are linked manually:

    /*
      This error you can ignore as it relates to manually linking the,
      react-native-firebase/app module instead of allowing auto linking
      that was introduced in the 6.0 update.
    */

11) After completing these steps navigate to:

    // Adding and creating the firebase credentials to your RN App
  - https://invertase.io/oss/react-native-firebase/quick-start/ios-firebase-credentials
