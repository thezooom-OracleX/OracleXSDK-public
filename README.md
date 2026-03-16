# OracleX SDK

오퍼월 SDK 연동 가이드입니다.

**현재 버전: v1.6.0**

---

## Android 연동

### 1. AAR 다운로드

[GitHub Releases](https://github.com/thezooom-OracleX/OracleXSDK-public/releases/latest)에서 `OracleXSDK.aar` 다운로드 후 `app/libs/`에 복사합니다.

### 2. build.gradle.kts 설정

```kotlin
dependencies {
    implementation(files("libs/OracleXSDK.aar"))
    implementation("androidx.appcompat:appcompat:1.6.1")
    implementation("androidx.browser:browser:1.7.0")
    implementation("com.google.android.gms:play-services-ads-identifier:18.0.1")
}
```

### 3. AndroidManifest.xml 권한 추가

```xml
<uses-permission android:name="android.permission.INTERNET" />
<!-- Android 13+ ADID 수집 권한 -->
<uses-permission android:name="com.google.android.gms.permission.AD_ID" />
```

---

## iOS 연동 (Swift Package Manager)

1. Xcode → **File → Add Package Dependencies**
2. URL 입력: `https://github.com/thezooom-OracleX/OracleXSDK-public`
3. Version: `1.6.0`

---

## 기본 사용법

### Android

```kotlin
import com.oraclex.sdk.OracleXSDK
import com.oraclex.sdk.OracleXConfig

OracleXSDK.init(
    context = this,
    config = OracleXConfig(
        channelUuid = "발급받은_채널_UUID",
        channelUserId = "사용자_고유_ID"
    )
)

// 오퍼월 열기
OracleXSDK.openOracleX()
```

### iOS

```swift
import OracleXSDK

OracleXSDK.shared.initialize(
    config: OracleXConfig(
        channelUuid: "발급받은_채널_UUID",
        channelUserId: "사용자_고유_ID"
    )
)

// 오퍼월 열기
OracleXSDK.shared.openOracleX()
```

---

## 에러 처리

```kotlin
// Android
OracleXSDK.setErrorListener { error ->
    Log.e("OracleX", "에러 [${error.code}]: ${error.message}")
}
```

```swift
// iOS
OracleXSDK.shared.setErrorListener { error in
    print("에러 [\(error.code)]: \(error.message)")
}
```

---

## 지원 환경

| 플랫폼 | 최소 버전 |
|--------|----------|
| Android | API 21 (Android 5.0) |
| iOS | iOS 13.0 |

---

## 연동 문의

SDK 연동 관련 문의는 담당자에게 연락해 주세요.
