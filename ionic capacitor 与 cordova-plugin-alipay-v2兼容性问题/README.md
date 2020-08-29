# cordova-plugin-alipay-v2

|环境|版本|
|:-----|:-----|
|@ionic/angular|5.0.0|
|cordova-plugin-alipay-v2|2.0.0|

```bash
 npm install cordova-plugin-alipay-v2
 npx cap sync
```

# `iOS` 部分

> ios/App/App/config.xml
- 追加 `<preference name="alipayid" value="your_$APP_ID"/>`

> ios/App/App/Info.plist
- `CFBundleURLTypes` 中追加
```
<dict>
    <key>CFBundleURLName</key>
    <string>alipay</string>
    <key>CFBundleURLSchemes</key>
    <array>
        <string>ali$APP_ID</string>
    </array>
</dict>
```
> ios/capacitor-cordova-ios-plugins/sources/CordovaPluginAlipayV2/alipay.m
- 修改 `pluginInitialize`
```
app_id = [[self.commandDelegate settings] objectForKey:@"alipayid"];
```
