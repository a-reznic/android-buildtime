# AndroidStudioBenchmark (Firefox Focus for Android)

`AndroidStudioBenchmark` contains a large codebase to measure the compilation time in `Android Studio`.

You are probably familiar with the following question:

"Should I buy an i5, i7, or even i9 processor for Android development? How much RAM would be enough? How SSD/M.2/NVMe influence build time?".

`AndroidStudioBenchmark` is initially created for my personal youtube channel
https://www.youtube.com/c/serhiyradkivskyi/about
to compare the performance of top laptops to choose the best system for `Android development`, because I hate to wait lot
of time waiting project to be built. And if we are buying laptop for 1000+ USD we want to be sure that it will perform 100% faster than our current machine. But online shops in there most - don't give ability to make real world
testing on your project to compare results. And most of tech reviewers describe laptops from designers/youtubers point of view,
not that much information from real software developers.

I believe the results will help developers to make the right cost/performance trade-off decision when choosing their next Mac/PC.
If you are interested - just continue reading and if you'll find this test useful - it would be very cool if you can share your result
and subscribe for my channel - it would be cool to have like minded audiance to share some more test on and get feedback on any
professional stuff.

# Results of Android Studio Performance testing:
https://buildtime.reznicsoftware.com
 
# Testing steps:

please modify(end of app/build.gradle file) the block - change deviceName and androidStudioVersion to your real values:
```groovy
buildTimeOptions {
    info {
        deviceName = "YOU PC NAME"
        androidStudioVersion = "Replace with your Android Studio version"
    }
}
```

# 1. Install Android Studio:
https://developer.android.com/studio

I was running test on `Android Studio Koala`, but you can run tests on the latest version (just write the version you have).
 
I have set 4Gb RAM for my android virtual machine.

And please remember your Android SDK location.

# 2. Download API Level 28 SDK for this do next:
Go to: `Tools -> SDK Manager`

Choose Tab: `SDK Platforms`

Select: `Android 9.0 (Pie) API Level 28` and download it.

Close `Android Studio` after this.

# 3. Install JDK 17:
https://www.oracle.com/java/technologies/downloads/?er=221886#java17

I have installed: `Java SE Development Kit` (You can also use JDK 11 or 17),

JDK 17 has support for Macbook with M1/MPro chips. It'w better use this if you have such machine, it will give faster results: (https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)

# 4. Set "JAVA_HOME" path in your Environment variables (System variables):
Doc https://www.baeldung.com/java-home-on-windows-mac-os-x-linux

# 5. Download android-buildtime repository:
https://github.com/a-reznic/android-buildtime

This is a fork of opensource `Firefox browser for Android` (https://github.com/mozilla-mobile/focus-android).

This is quite a big project (after all gradle modules downloaded it weights 6+Gb).

You can download it as zip file to you fast SSD location.

Unzip it.

# 6. Restart you system.
Then make sure that no other programs/antivirus/browsers/big massive custom processes running.

Make sure that system is quite idle.

# 7. Open Android Studio.
Go to `File -> Open`: select Firefox Focus for Android project from your location and open it.

`Wait while all gradle files will be synced`, it can take up to 5-10 minutes.

# 8. Run next command to test speed of your machine doing next work:
Go to: `View -> Tools Windows -> Terminal`

please modify(end of app/build.gradle file) the block - change deviceName and androidStudioVersion to your real values:
```groovy
buildTimeOptions {
    info {
        deviceName = "YOU PC NAME"
        androidStudioVersion = "Replace with your Android Studio version"
    }
}
```

Type command and press enter:

Windows:
  ```shell
  gradlew clean assemble 
  ```

MacOS/Linux:
  ```shell
  ./gradlew clean assemble 
  ```

Wait for assembling to complete. Run it 4 times in a row.

First time it will be your fresh build and it will take a little longer. Two next builds will be normal one.

After each build completes make a screenshot and save time result.

While system assembling watch for you `Task Manager` how `CPU` is processing, how much `RAM` is used,
it would be cool if you can watch CPU temperature with some tool like `AIDA`: https://www.aida64.com/downloads

# All results will be sent to the server 
You can see results of all tests here: https://buildtime.reznicsoftware.com

You Device result: https://buildtime.reznicsoftware.com/device/{device_id} - response from server

