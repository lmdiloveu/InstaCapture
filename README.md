别人写的一个module，屏幕截屏
# InstaCapture v0.3
Android library to capture screenshot from your app

### Fast Usage
- Capture a screenshot by one line of code!
```java
InstaCapture.getInstance(this).capture();
```

### Features
- Capture all the contents of the screen, includes:
   - Google Maps ([MapView](https://developers.google.com/android/reference/com/google/android/gms/maps/MapView), [SupportMapFragment](https://developers.google.com/android/reference/com/google/android/gms/maps/SupportMapFragment)) 
   - Dialogs
- No need to set your dialog or your google maps to InstaCapture, just call capture() method.
- Set a specific view(s) to prevent it from capturing.
- No permissions are required.


### Installation

Add this to your module `build.gradle` file:
```gradle
dependencies {
	...
	 compile 'com.github.tarek360:instacapture:0.3'
}
```

Add this to your root `build.gradle` file (**not** your module `build.gradle` file):
```gradle
allprojects {
	repositories {
		...
		maven { url "https://jitpack.io" }
	}
}
```


### Usage in details

- To capture a screenshot with ScreenCaptureListener.
```java
   InstaCapture.getInstance(this).setScreenCapturingListener(new ScreenCaptureListener() {

      @Override public void onCaptureStarted() {
          //TODO..
      }
      @Override public void onCaptureFailed(Throwable e) {
          //TODO..
      }
      @Override public void onCaptureComplete(File file) {
          //TODO..
      }
    }).capture();
```


- To ignore view(s) from the screenshot.
```java
.capture(ignoredView); // view(s) must have id(s), the views which have no ids will not be ignored.
```


- By default screenshots are save to the filesystem directory on the internal storage, but you can captuer screenshot into your file.
```java
.capture(file);
```


- To captuer screenshot into your file and ignore view(s) from it.
```java
.capture(file, ignoredView); // view(s) must have id(s), the views which have no ids will not be ignored.
```


- To enable logging.
```java
InstaCaptureConfiguration config = new InstaCaptureConfiguration.Builder().logging(true).build();
InstaCapture.setConfiguration(config);
```



## License

>Copyright 2016 Tarek360

>Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

>   http://www.apache.org/licenses/LICENSE-2.0

>Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
