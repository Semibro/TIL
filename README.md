# TIL (Today I Learn)

<br>

## 2023. 09. 11

```
현재 React Native 기반의 AR 애플리케이션을 개발 중이다.

하지만, 개발 과정에서 AR Core의 마지막 업데이트가 2년 전임을 알게 됐다.

그래서 다른 방법을 모색하던 중..! react-native-vision-camera에 대해서 알게 되었고, 해당 라이브러리를 사용해 AR과 비스무리한(?) 기능을 구현하고자 한다.

근데 이것조차 쉽지 않은게 react-native와 호환성 문제가 많이 발생한다.

(에러 내용은 하단에 첨부)

프로젝트를 위해 빠른 시일 내 해결해야 하는데, 추후 해결하면 해결 방법을 적어 볼 예정.
```

```
Configure project :react-native-reanimated
No AAR for react-native-reanimated found. Attempting to build from source.
Android gradle plugin: 7.4.2
Gradle: 8.0.1
WARNING:Software Components will not be created automatically for Maven publishing from Android Gradle Plugin 8.0. To opt-in to the future behavior, set the Gradle property android.disableAutomaticComponentCreation=true in the `gradle.properties` file or use the new publishing DSL.

> Configure project :react-native-vision-camera
[VisionCamera] react-native-worklets-core found, Frame Processors enabled!
WARNING:The specified Android SDK Build Tools version (30.0.1) is ignored, as it is below the minimum supported version (30.0.3) for Android Gradle Plugin 7.4.2.
Android SDK Build Tools 30.0.3 will be used.
To suppress this warning, remove "buildToolsVersion '30.0.1'" from your build.gradle file, as each version of the Android Gradle Plugin now has a default version of the build tools.

> Task :react-native-reanimated:processDebugManifest
package="com.swmansion.reanimated" found in source AndroidManifest.xml: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-reanimated\android\src\main\AndroidManifest.xml.
Setting the namespace via a source AndroidManifest.xml's package attribute is deprecated.
Please instead set the namespace (or testNamespace) in the module's build.gradle file, as described here: https://developer.android.com/studio/build/configure-app-module#set-namespace
This migration can be done automatically using the AGP Upgrade Assistant, please refer to https://developer.android.com/studio/build/agp-upgrade-assistant for more information.

> Task :react-native-vision-camera:processDebugManifest
package="com.mrousavy.camera" found in source AndroidManifest.xml: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-vision-camera\android\src\main\AndroidManifest.xml.
Setting the namespace via a source AndroidManifest.xml's package attribute is deprecated.
Please instead set the namespace (or testNamespace) in the module's build.gradle file, as described here: https://developer.android.com/studio/build/configure-app-module#set-namespace
This migration can be done automatically using the AGP Upgrade Assistant, please refer to https://developer.android.com/studio/build/agp-upgrade-assistant for more information.

> Task :react-native-worklets-core:processDebugManifest
package="com.worklets" found in source AndroidManifest.xml: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-worklets-core\android\src\main\AndroidManifest.xml.
Setting the namespace via a source AndroidManifest.xml's package attribute is deprecated.
Please instead set the namespace (or testNamespace) in the module's build.gradle file, as described here: https://developer.android.com/studio/build/configure-app-module#set-namespace
This migration can be done automatically using the AGP Upgrade Assistant, please refer to https://developer.android.com/studio/build/agp-upgrade-assistant for more information.

> Task :vision-camera-image-labeler:processDebugManifest
package="com.visioncameraimagelabeler" found in source AndroidManifest.xml: C:\Users\SSAFY\Desktop\frontend\node_modules\vision-camera-image-labeler\android\src\main\AndroidManifest.xml.
Setting the namespace via a source AndroidManifest.xml's package attribute is deprecated.
Please instead set the namespace (or testNamespace) in the module's build.gradle file, as described here: https://developer.android.com/studio/build/configure-app-module#set-namespace
This migration can be done automatically using the AGP Upgrade Assistant, please refer to https://developer.android.com/studio/build/agp-upgrade-assistant for more information.

> Task :react-native-reanimated:compileDebugJavaWithJavac

> Task :react-native-vision-camera:compileDebugKotlin
'compileDebugJavaWithJavac' task (current target is 11) and 'compileDebugKotlin' task (current target is 1.8) jvm target compatibility should be set to the same Java version.
w: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-vision-camera\android\src\main\java\com\mrousavy\camera\CameraView+Events.kt: (7, 44): 'RCTEventEmitter' is deprecated. Deprecated in Java
w: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-vision-camera\android\src\main\java\com\mrousavy\camera\CameraView+Events.kt: (13, 28): 'RCTEventEmitter' is deprecated. Deprecated in Java
w: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-vision-camera\android\src\main\java\com\mrousavy\camera\CameraView+Events.kt: (13, 57): 'receiveEvent(Int, String!, WritableMap?): Unit' is deprecated. Deprecated in Java
w: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-vision-camera\android\src\main\java\com\mrousavy\camera\CameraView+Events.kt: (31, 28): 'RCTEventEmitter' is deprecated. Deprecated in Java
w: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-vision-camera\android\src\main\java\com\mrousavy\camera\CameraView+Events.kt: (31, 57): 'receiveEvent(Int, String!, WritableMap?): Unit' is deprecated. Deprecated in Java
w: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-vision-camera\android\src\main\java\com\mrousavy\camera\CameraView+Events.kt: (37, 28): 'RCTEventEmitter' is deprecated. Deprecated in Java
w: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-vision-camera\android\src\main\java\com\mrousavy\camera\CameraView+Events.kt: (37, 57): 'receiveEvent(Int, String!, WritableMap?): Unit' is deprecated. Deprecated in Java
w: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-vision-camera\android\src\main\java\com\mrousavy\camera\core\CameraSession.kt: (209, 9): Variable 'previewOutput' is never used
w: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-vision-camera\android\src\main\java\com\mrousavy\camera\core\RecordingSession.kt: (49, 96): 'constructor MediaRecorder()' is deprecated. Deprecated in Java
w: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-vision-camera\android\src\main\java\com\mrousavy\camera\extensions\CameraCharacteristics+getOutputSizes.kt: (46, 36): 'get(Int, Int): CamcorderProfile!' is deprecated. Deprecated in Java
w: C:\Users\SSAFY\Desktop\frontend\node_modules\react-native-vision-camera\android\src\main\java\com\mrousavy\camera\extensions\CameraDevice+createCaptureSession.kt: (92, 12): 'createCaptureSessionByOutputConfigurations((Mutable)List<OutputConfiguration!>!, CameraCaptureSession.StateCallback!, Handler?): Unit' is deprecated. Deprecated in Java

> Task :vision-camera-image-labeler:compileDebugJavaWithJavac FAILED

Deprecated Gradle features were used in this build, making it incompatible with Gradle 9.0.

You can use '--warning-mode all' to show the individual deprecation warnings and determine if they come from your own scripts or plugins.

See https://docs.gradle.org/8.0.1/userguide/command_line_interface.html#sec:command_line_warnings
87 actionable tasks: 82 executed, 5 up-to-date

info 💡 Tip: Make sure that you have set up your development environment correctly, by running react-native doctor. To read more about doctor command visit: https://github.com/react-native-community/cli/blob/main/packages/cli-doctor/README.md#doctor

Note: Some input files use or override a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
Note: Some input files use unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.
C:\Users\SSAFY\Desktop\frontend\node_modules\vision-camera-image-labeler\android\src\main\java\com\visioncameraimagelabeler\VisionCameraImageLabelerPackage.java:19: error: cannot find symbol
    FrameProcessorPlugin.register(new VisionCameraImageLabelerPlugin());
                        ^
  symbol:   method register(VisionCameraImageLabelerPlugin)
  location: class FrameProcessorPlugin
C:\Users\SSAFY\Desktop\frontend\node_modules\vision-camera-image-labeler\android\src\main\java\com\visioncameraimagelabeler\VisionCameraImageLabelerPlugin.java:24: error: VisionCameraImageLabelerPlugin is not abstract and does not override abstract method callback(Frame,Map<String,Object>) in FrameProcessorPlugin
public class VisionCameraImageLabelerPlugin extends FrameProcessorPlugin {
       ^
C:\Users\SSAFY\Desktop\frontend\node_modules\vision-camera-image-labeler\android\src\main\java\com\visioncameraimagelabeler\VisionCameraImageLabelerPlugin.java:27: error: method does not override or implement a method from a supertype
  @Override
  ^
C:\Users\SSAFY\Desktop\frontend\node_modules\vision-camera-image-labeler\android\src\main\java\com\visioncameraimagelabeler\VisionCameraImageLabelerPlugin.java:54: error: constructor FrameProcessorPlugin in class FrameProcessorPlugin cannot be applied to given types;
    super("labelImage");
    ^
  required: no arguments
  found: String
  reason: actual and formal argument lists differ in length
4 errors

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':vision-camera-image-labeler:compileDebugJavaWithJavac'.
> Compilation failed; see the compiler error output for details.

* Try:
> Run with --stacktrace option to get the stack trace.
> Run with --info or --debug option to get more log output.
> Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 25s
error Failed to install the app.
info Run CLI with --verbose flag for more details.
```
