# 1.7.4-sylvain-offline

Adjusts Sylvain camera preview compensation by 180 degrees for barcode scanning, palm enrollment and identification. Text, overlays, Activity orientation, PalmAPI input rotation and barcode input rotation remain unchanged. No public API changes.

```gradle
implementation "com.palmid:native_sdk:1.7.4-sylvain-offline"
```

Source commit: `a3e602579905e31ed8044b18923e0c51615db9e5` on `release/1.7.4-sylvain-offline` in `palmid-sdk-native`.

Built on macOS with Flutter 3.27.4, JDK 17 and Gradle 8.11.1, using the preserved 1.7.3 release source baseline, the Sylvain entrypoint, `RESULT_PALM_MODEL=true` and Native PRODUCT mode.

## Binary integrity

[integrity.json](integrity.json) contains SHA-256 hashes for every published AAR and every bundled `.so`, compared with released `1.7.3-sylvain-offline`.

- All 14 device/algorithm native libraries are byte-identical to 1.7.3: `libPalmAPI.so`, `libaffinity_manager_ndk.so`, `libc++_shared.so`, `libomp.so`, `libpalm_wrapper.so`, `libstream_jni.so` and `libveinshine_utils.so`, each for arm64-v8a and armeabi-v7a.
- Only Flutter `libapp.so` changes, for arm64-v8a, armeabi-v7a and x86_64. These files contain the updated preview code, so their hashes necessarily differ.
- The Flutter engine dependency is unchanged.
- All 9 AAR archives and their versioned dependency closure were verified. Existing published version directories are preserved.

## Validation

Four rotation tests passed. Flutter and Native release AAR builds and MainMoney Android integration build passed. On P105, barcode, enrollment and identification previews opened; the MainMoney barcode preview changed by 180 degrees while text and layout stayed unchanged. Real-palm orientation, successful recognition and the bound MainMoney payment flow have not yet been confirmed in this release's device test.
