![](https://github.com/TutorialsAndroid/progressx/blob/master/sample/src/main/res/mipmap-xxhdpi/ic_launcher.png)

# ProgressX ![API](https://img.shields.io/badge/API-21%2B-brightgreen.svg?style=flat) [![Known Vulnerabilities](https://snyk.io/test/github/TutorialsAndroid/progressx/badge.svg?targetFile=library%2Fbuild.gradle)](https://snyk.io/test/github/TutorialsAndroid/progressx?targetFile=library%2Fbuild.gradle) [![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-ProgressX-orange.svg?style=flat-square)](https://android-arsenal.com/details/1/7589) [![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

A material style progress wheel that you can integrate into your app

**Library available at JitPack.io**

[![](https://jitpack.io/v/TutorialsAndroid/progressx.svg)](https://jitpack.io/#TutorialsAndroid/progressx)

`Latest version of this library is migrated to androidx`

**Sample Screen**

![](https://github.com/TutorialsAndroid/progressx/blob/master/art/device-2019-03-23-154713.png)

## Download

Add it in your root build.gradle at the end of repositories:

	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}

Step 2. Add the dependency

	dependencies {
	        implementation 'com.github.TutorialsAndroid:progressx:v4.0.19'
	}

## Usage

You can create your own progress wheel in xml like this (remeber to add ```xmlns:wheel="http://schemas.android.com/apk/res-auto"```):

```xml
<com.developer.progressx.ProgressWheel
        android:id="@+id/progress_wheel"
        android:layout_width="80dp"
        android:layout_height="80dp"
        android:layout_centerHorizontal="true"
        android:layout_centerVertical="true"
        wheel:matProg_barColor="#5588FF"
        wheel:matProg_progressIndeterminate="true" />
```

Or in code:

```Java
ProgressWheel wheel = new ProgressWheel(context);
wheel.setBarColor(Color.BLUE);
...

```

### Callback

Use ```setCallback(ProgressCallback)``` to assign a callback that will be called each time the progress changes. This way you can update a value on the progress alongside with the progress animation, or execute an action once the progress reaches a certain value. in the indeterminatge wheel, the callback is called with a value of -1.0f every time the animation cycle finishes (when the wheel shrinks back to its smaller size).

### Indeterminate wheel

For making the wheel indeterminate, just call the ```spin()``` method. If you set a progress value, the wheel will stop spinning.

You have two methods for setting the progress:

```progressWheel.setProgress(float value)```

Sets the value, and the wheel will smoothly animate to that value. The speed of the animation is defined by the spinSpeed (can be set with ```setSpinSpeed```, which number is the number of full turns per second)

```progressWheel.setInstantProgress(float value)```

Sets the value, and the wheel will instantly move to that value.

You can change other wheel properties such as the progress bar color, the wheel's background or the wheel's size and width.

### Fill radius

In case you want the spinning wheel to fill the whole layout instead of having a fixed size, you can use ```matProg_fillRadius```.

```xml
<com.developer.progressx.ProgressWheel
        android:id="@+id/progress_wheel"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_centerHorizontal="true"
        android:layout_centerVertical="true"
        wheel:matProg_barColor="#5588FF"
        wheel:matProg_progressIndeterminate="true"
        wheel:matProg_fillRadius="true" />
```

This way, the wheel will be as big as the parent layout. Be warned though, if the parentlayout is not square, the wheel will become an oval since the wheel will always adapt to fill the parent view.

### Other options

In the xml definition, besides the ```fillRadius``` property, you can set:

* `matProg_progressIndeterminate: boolean`, if you want the wheel to spin right away.
* `matProg_barColor: color`, sets the small bar's color (the spinning bar in the indeterminate wheel, or the progress bar)
* `matProg_barWidth: dimension`, the width of the spinning bar
* `matProg_rimColor: color`, the wheel's border color
* `matProg_rimWidth: dimension`, the wheel's width (not the bar)
* `matProg_spinSpeed: float`, the base speed for the bar in indeterminate mode, and the animation speed when setting a value on progress. The speed is in full turns per second, this means that if you set speed as 1.0, means that the bar will take one second to do a full turn.
* `matProg_barSpinCycleTime: integer`, the time in milliseconds the indeterminate progress animation takes to complete (extending and shrinking the bar while spinning)
* `matProg_circleRadius: dimension`, the radius of the progress wheel, it will be ignored if you set fillRadius to true
* `matProg_fillRadius: boolean`, set to true if you want the progress wheel to fill the whole layout
* `matProg_linearProgress: boolean`, set to true if you want a linear animation on the determinate progress (instead of the interpolated default one).

```
Copyright 2019 ProgressX

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

 http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
