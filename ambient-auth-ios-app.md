---
id: ambient-auth-ios-app
tags: #objc, TODO
title: Ambient Auth iOS App
---

The app only needs to target iOS 5.0 and above on devices with a 5 megapixel+ camera. This is due to the fact that decoding QR becomes problematic with low-res imagery.

And though [UIWebView](http://developer.apple.com/library/ios/#DOCUMENTATION/StringsTextFonts/Conceptual/TextAndWebiPhoneOS/DisplayWebContent/DisplayWebContent.html) could be used to display certain elements, it should be a fully native app written in Objective-C for consistency and performance. Useful libraries to build the app include:

* [ZBar](http://zbar.sourceforge.net/) — provides a QR decoder.

And, given the [known weaknesses of the iOS Keychain](http://sit.sit.fraunhofer.de/studies/en/sc-iphone-passwords-faq.pdf), users should optionally be able to set an additional passcode to unlock the Ambient Auth app — thus extending the potential time it could take an attacker to gain access to sensitive data.