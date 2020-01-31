

[![Build Status](https://img.shields.io/badge/platform-android-green)](https://img.shields.io/badge/platform-android-green)
[![Build Status](https://img.shields.io/badge/type-library-blue)](https://img.shields.io/badge/type-library-blue)


# LivenessSDK
LivenessSDK for Android

## Index
{:toc}

## 🌟 Features
- Supports Android 5.0+


## 📲 Installation
Requires Java8 support/ gradle plugin 3+

#### Using [ AAR  (Android Archive)]([https://developer.android.com/studio/projects/android-library](https://developer.android.com/studio/projects/android-library))

An **AAR file** contains a software library used for developing Android apps. It is structurally similar to an . APK **file** (Android Package), but it allows a developer to store a reusable component that can be used across multiple different apps. To integrate AAR  into your android project:

- Clone the entire repo
- Open android studio and add the liveness SDK to your android project
  - Click  `File > New > New Module`.
  - Click `Import .JAR/.AAR Package` from repo directory then click `Next`.
  -  Enter the location of the `liveness.aar` file in the cloned directory then click `Finish`
- Make sure the library is listed at the top of your `settings.gradle` file, as shown here for a library named "liveness":
  -  `include ':app',  ':liveness'`
 - Open the app module's `build.gradle` file and add a new line to the `dependencies` block as shown in the following snippet:
   - `dependencies { implementation project(":liveness")  
}`

## 🐒 How to use
- Make sure to get the camera permission.
#### Kotlin
```kotlin
  
import io.facex.liveness.Liveness  
import io.facex.liveness.LivenessListener

class MainActivity : AppCompatActivity(),LivenessListener{
   
private lateinit var liveness: Liveness

 override fun livenessError(live: Boolean?, errorMessage: String?) {   
}  

override fun livenessSuccess(live: Boolean?,bitmap : Bitmap) {  
 
}
override fun onCreate(savedInstanceState: Bundle?) {
	liveness= Liveness(this, R.id.fragment_holder)
	liveness.Eyes=true
	liveness.Mouth=true
	....
	liveness.startLiveness()
  }
}

```
## Interfaces

#### LivenessListener 

```kotlin

 override fun livenessSuccess(live: Boolean?,bitmap : Bitmap) {
  }
  
 override fun livenessError(live: Boolean?, errorMessage: String?) {
  }

```

## 🎛 Customization

You can set some properties for liveness.

#### Steps
| Steps | Value | Default | 
| ------- | ------- |------- | 
| **Eyes** | `Boolean` | `true` | 
| **Mouth**  | `Boolean` | `true` | 
| **Yaw** | `Boolean` | `true` | 
| **Random**  | `Boolean` | `true` | 


#### Thresholds
| Property | Values | Default | 
| ------- | ------- |------- | 
| **EYE_THRESHOLD**  | `0.0 ... 6.0` | `3.0` | 
| **MOUTH_THRESHOLD**  | `2.0 ... 9.0` | `6.0` | 
| **TIMER**   | `Seconds` | `5 seconds` | 
| **MAX_TIMER**   | `Seconds` | `15 seconds` |




### 📋 Supported OS & SDK Versions
* Android 5.0+
* Java 8