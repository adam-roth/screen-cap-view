### IAScreenCaptureView

An iOS UIView subclass that records its contents to MPEG-4 video.

### Building

To use this code simply add the sources to your project and then ensure that your build 
includes the following Frameworks:

* AssetsLibrary
* AVFoundation
* CoreGraphics
* CoreMedia
* CoreVideo
* QuartzCore

### Usage

To use this code, you must perform the following steps:

1.  Set up an `IAScreenCaptureView` instance as the parent view of the view(s) you want to record.

2.  Implement the `IAScreenCaptureViewDelegate` protocol and set the `delegate` property on your `IAScreenCaptureView` instance (this step is optional; you only need to do it if you care about getting your captured video output).

3.  Call `startRecording` when you are ready to start capturing video.

4.  Call `stopRecording` when you are done recording video.  Your delegate will receive the path to the completed video file, which you can then copy off to wherever you prefer.

Note that you can also call `currentScreen` to grab a screenshot of the view's current state.  This works whether or not you are currently recording.
    

### Limitations

There are a few limitations to be aware of when using this class:

1.  If you want to record a `UIScrollView` you need to implement your `UIScrollViewDelegate` such that it calls `setNeedsDisplay` on the `IAScreenCaptureView` while the `UIScrollView` is scrolling. 

2.  Currently only video is captured.  It should be possible to capture video as well as audio, but I have not had time to add this functionality.  If you happend to add it, feel free to send a pull request.

3.  I have not tested this class to see if it can record OpenGL-based views.  I suspect that it probably cannot, however. 

4.  I have not tested this code heavily on actual iOS devices (it's primarily seen duty in the iOS simulator).  It should run, but I cannot make any guarantees with respect to its level of performance.  I would not expect it to be particularly fast or particularly light on battery consumption.

### FAQ

**_Why create this utility?_**<br />
It's a funny story, actually.  I was reviewing some work submitted by an overseas contractor; it was full of bugs, the vast majority graphical.  Many of them only appeared when interacting with the UI in a particular way.  Textual descriptions of the issues were too clunky, and even screenshots were inadequate at properly documenting and describing the nature of the issues.  So I implemented this class so that I could quickly and easily record a video for each UI bug that I found.

That said, this thing probably works just as good at created demo videos as it does for pointing out bugs.

**_Why should I use this library?_**<br />
This code works reasonably well for capturing screen content.  Use it if you want to do that.

**_Why should I NOT use this library?_**<br />
Don't use this code if you don't need to record your app's screen content.  Also don't use it if you want your app to run fast and not waste the device's battery.  Pertty much don't use it in production at all, unless you're building a screen-capture app.

**_What are your license terms?_**<br />
Use this code if you want, otherwise don't.  That's it.  
