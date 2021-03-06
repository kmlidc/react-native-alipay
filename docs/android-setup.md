# Android Setup

1. Open up `android/app/src/main/java/[...]/MainApplication.java`, add `new AlipayPackage()` to the list returned by the `getPackages()` method like this:
```java
// ...

import com.reactlibrary.AlipayPackage;

public class MainApplication extends Application implements ReactApplication {

  private final ReactNativeHost mReactNativeHost = new ReactNativeHost(this) {

    // ...

    @Override
    protected List<ReactPackage> getPackages() {
      return Arrays.<ReactPackage>asList(
        new MainReactPackage(),
        new AlipayPackage() // Add this line
      );
    }
  };

  // ...
}
```

2. Append the following lines to `android/settings.gradle`:
```gradle
include ':react-native-alipay'
project(':react-native-alipay').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-alipay/android')
```

3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
```gradle
    compile project(':react-native-alipay')
```

4. Append the following lines to `android/app/proguard-rules.pro`
```
-keep class com.alipay.** { *; }
```
