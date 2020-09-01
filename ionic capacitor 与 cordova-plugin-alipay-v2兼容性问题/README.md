# cordova-plugin-alipay-v2

- [本地修复仓库](http://192.168.3.168:12000/tool/cordova-plugin-alipay-v2)

|环境|版本|
|:-----|:-----|
|@ionic/angular|5.0.0|
|cordova-plugin-alipay-v2|2.0.0|

```bash
 npm install git+http://192.168.3.168:12000/tool/cordova-plugin-alipay-v2.git
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

# 使用方法
```
declare var cordova: any;
cordova.plugins.alipay.payment(params, successHandler, errorHandler)
```
