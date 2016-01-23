# react-native-modal-android
The <Modal /> component has the same API as on iOS - http://facebook.github.io/react-native/docs/modal.html#content
The animated prop is not implemented yet.
I just wrap that PR code which will ship with react-native for react-native 0.18- 
The origin author is satya164 @ https://github.com/satya164

[![npm version](http://img.shields.io/npm/v/react-native-modal-android.svg?style=flat-square)](https://npmjs.org/package/react-native-modal-android "View this project on npm")
[![npm downloads](http://img.shields.io/npm/dm/react-native-modal-android.svg?style=flat-square)](https://npmjs.org/package/react-native-modal-android "View this project on npm")
[![npm licence](http://img.shields.io/npm/l/react-native-modal-android.svg?style=flat-square)](https://npmjs.org/package/react-native-modal-android "View this project on npm")

### Installation

```bash
npm install react-native-modal-android --save
```

### Add it to your android project

* In `android/setting.gradle`

```gradle
...
include ':react-native-modal-android', ':app'
project(':react-native-modal-android').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-modal-android')
```

* In `android/app/build.gradle`

```gradle
...
dependencies {
  ...
  compile project(':react-native-modal-android')
}
```

* Register Module (in MainActivity.java)

```java
import cn.tuofeng.modalhost.ReactModalHostPackage;  // <--- import

public class MainActivity extends Activity implements DefaultHardwareBackBtnHandler {
  ......

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    mReactRootView = new ReactRootView(this);

    mReactInstanceManager = ReactInstanceManager.builder()
      .setApplication(getApplication())
      .setBundleAssetName("index.android.bundle")
      .setJSMainModuleName("index.android")
      .addPackage(new MainReactPackage())
      .addPackage(new ReactModalHostPackage()) // <------ add this line to yout MainActivity class
      .setUseDeveloperSupport(BuildConfig.DEBUG)
      .setInitialLifecycleState(LifecycleState.RESUMED)
      .build();

    mReactRootView.startReactApplication(mReactInstanceManager, "AndroidRNSample", null);

    setContentView(mReactRootView);
  }

  ......

}
```

More info here: https://github.com/facebook/react-native/pull/5320

## License
MIT
