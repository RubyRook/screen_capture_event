# Screen Capture Event
Catch screen capture (Screenshot & Screen Record) event for Android and iOS, Yes... Screen record is working for Android! 🙌

## Recipe
You can catch capture event by simply writing these codes

```dart
final ScreenCaptureEvent screenListener = ScreenCaptureEvent();


@override
void initState() {
    screenListener.addScreenRecordListener((recorded) {
        ///Recorded was your record status (bool)
        setState(() {
            text = recorded ? "Start Recording" : "Stop Recording";
        });
    });

    screenListener.addScreenShotListener((filePath) {
        ///filePath only available for Android
        setState(() {
            text = "Screenshot stored on : $filePath";
        });
    });

    ///You can add multiple listener ^-^
    screenListener.addScreenRecordListener((recorded) {
        print("Hi i'm 2nd Screen Record listener");
    });
    screenListener.addScreenShotListener((filePath) {
        print("Wohooo i'm 2nd Screenshot listener");
    });

    ///Start watch
    screenListener.watch();
    super.initState();
}

@override
void dispose() {
    ///Don't forget to dispose it to detach all the observer :)
    screenListener.dispose();
    super.dispose();
}
```

You also can secure Android screen by prevent user to take screenshot or screen record, simply write this code

```dart
screenListener.preventAndroidScreenShot(true);
```

Take a look at docs and example code to get further information, PRs are very welcome 🙌


## Note
I don't own this package. It just a copy and update namespace for use with new version of flutter due to owner not active.  

