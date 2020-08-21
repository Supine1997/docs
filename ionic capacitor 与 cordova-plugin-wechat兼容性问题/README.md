# cordova-plugin-wechat `Android`

> 与capacitor存在兼容性问题 需按照以下步骤手动配置

|环境|版本|
|:-----|:-----|
|@ionic/angular|4.10.0|
|@ionic-native/wechat|5.19.1|
|cordova-plugin-wechat|2.9.0|

> install
```bash
 npm install @ionic-native/wechat
 npm install cordova-plugin-wechat
 npx cap sync
```

> Activity

拷贝 `node_modules/cordova-plugin-wechat/src/android/` 目录下 `EntryActivity.java` , `WXEntryActivity.java` , `WXPayEntryActivity.java` 至 `android\app\src\main\java\com\globletech\masses\wxapi`

> Wechat.java

修改 `android/capacitor-cordova-android-plugins/src/main/java/xu/li/cordova/wechat/Wechat.java`
```
public static String getAppId(CordovaPreferences f_preferences) {
    //if (appId == null) {
    //    if(f_preferences != null) {
    //        appId = f_preferences.getString(WXAPPID_PROPERTY_KEY, "");
    //    }else if(wx_preferences != null){
    //        appId = wx_preferences.getString(WXAPPID_PROPERTY_KEY, "");
    //    }
    //}
    //return appId;
    //无法读取配置$WECHATAPPID 故直接返回
    return $WECHATAPPID;
}
```

> AndroidManifest

剪切 `android\capacitor-cordova-android-plugins\src\main\AndroidManifest.xml` 中
```
<activity android:name=".wxapi.WXEntryActivity" android:label="@string/launcher_name" android:exported="true" android:taskAffinity="com.globletech.masses" android:launchMode="singleTask">
  <intent-filter>
    <action android:name="android.intent.action.VIEW"/>
    <category android:name="android.intent.category.DEFAULT"/>
    <data android:scheme="$WECHATAPPID"/>
  </intent-filter>
</activity>
<activity android:name=".wxapi.WXPayEntryActivity" android:label="@string/launcher_name" android:exported="true" android:launchMode="singleTop">
  <intent-filter>
    <action android:name="android.intent.action.VIEW"/>
    <category android:name="android.intent.category.DEFAULT"/>
    <data android:scheme="$WECHATAPPID"/>
  </intent-filter>
</activity>
```
粘贴至 `android\app\src\main\AndroidManifest.xml` 追加至application里
并修改 `$WECHATAPPID` 为正确的WECHATAPPID,
修改 `@string/launcher_name` 为 `@string/app_name`

> build.gradle

`android\app\build.gradle` 中 `dependencies` 下添加
```
implementation 'org.apache.cordova:framework:7.0.0'
```
