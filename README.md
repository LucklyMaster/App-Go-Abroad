# 接入文档
## [AppsFlyer](https://dev.appsflyer.com/hc) 
+ 引入SDK
    ```
    repositories {
        mavenCentral()
    }
    dependencies {
        implementation 'com.appsflyer:af-android-sdk:6.3.2' 
    }
    //权限
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    //混淆
    -keep class com.appsflyer.** { *; }
    -keep public class com.android.installreferrer.** { *; }
    ```
+ 启动SDK
    ```
    AppsFlyerLib.getInstance()
            .init(Constants.APPSFLYER_DEV_KEY, null, this)
            .apply { setDebugLog(BuildConfig.DEBUG) }
            .start(instance, Constants.APPSFLYER_DEV_KEY, object : AppsFlyerRequestListener {
                override fun onSuccess() {
                    LogUtils.d("AppsFlyerLib启动成功")
                }

                override fun onError(code: Int, msg: String) {
                    LogUtils.d("AppsFlyerLib启动失败（code = $code,msg = $msg）")
                }
            })
    ```
+ 已知问题
