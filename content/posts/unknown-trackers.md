---
title: "Unknown tracker alerts: a feature locked away in Google-land?"
date: 2023-08-05T03:10:56+06:00
draft: false

tags:
 - Tech
---

With this recent [blog post](https://blog.google/products/android/unknown-tracker-alert-google-android/), Google highlighted Android's new capability to detect Bluetooth-powered trackers and one thing showcased is its [manual scan feature](https://support.google.com/android/?p=manual_scan) and while Apple previously published its [Tracker Detect](https://play.google.com/store/apps/details?id=com.apple.trackerdetect) app on the Play Store in late-2021 for AirTag-compatible devices, [Google's initiative](https://arstechnica.com/gadgets/2023/05/apple-and-google-submit-joint-proposal-to-fight-malicious-use-of-tracking-devices/) might be driven by the development of joint-specification of such devices in which Apple had its input. However, taking advantage of it is hindered by the feature's discoverability in the Android world, regardless of Google's intention.

## GrapheneOS
On systems running Android 12 or above, users can access the features by going to _Settings → Safety & emergency → Unknown tracker alerts_. These appear to be part of Google Mobile Services (GMS) and as someone running GrapheneOS (based on Android 13 platform), I could not find it placed neatly in Settings app but like suggested for devices running Android 11 or below, these are tucked away inside its 'Google settings' sub-page which you only have access to if you have Google Play Services installed. In the end, what I discovered is that you would have to go to _Settings → Apps → Sandboxed Google Play → Google Settings → Personal Safety → Unknown tracker alerts_ to access them. 

## OneUI
Another device I had had been a Samsung Galaxy running OneUI 4.1 (with Android 12 underneath) and here the steps should have been simpler: _Settings → Google → Google Settings → Personal Safety → Unknown tracker alerts_ but the last page had been missing even though it should have been there because of these features being supported on Android 11 or older. One possibility would have been that the device had outdated software as its Android security patch level was set to Nov 2022. But updating it to OneUI 5.1 with July 2023 patch level did not work.


This marks another set of features not accessible to people who either do not have access to Google apps/services or simply refuse to do so. But all is not lost. Apps like [BLE Radar](https://apt.izzysoft.de/fdroid/index/apk/f.cking.software) and [AirGuard](https://f-droid.org/en/packages/de.seemoo.at_tracking_detection/) are there to fill in the gap.
