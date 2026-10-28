# TouchTalk Ultra — fresh Android project

A new native Android (Java + Android Views) foundation, intentionally avoiding Jetpack Compose and Kotlin compiler compatibility issues.

## Included in this starter
- Home dashboard and five-tab navigation: Home, Talk, Device, Insights, Settings
- Bright/dark appearance, accent colour selection, larger text preference
- Type-to-speech, Android speech recognition, quick phrases
- Six-dot Braille pad (basic English/Braille character mapping)
- Paired Bluetooth Classic device picker using the standard SPP UUID
- Newline-delimited UTF-8 send and receive; optional automatic speech for received lines
- Recent activity list and basic connection diagnostics
- GitHub Actions workflow that builds and uploads a debug APK artifact

## Build
Open this folder in Android Studio, allow Gradle sync, then run the `app` configuration. Or push to GitHub and run **Actions → Build TouchTalk Ultra APK**. The resulting artifact is named `TouchTalk-Ultra-debug-apk`.

## ESP32 integration notes
- Pair the ESP32 with Android in system Bluetooth settings before connecting from the app.
- The app currently sends typed messages as UTF-8 followed by `\n` over Bluetooth Classic SPP and treats each received newline-delimited line as a message.
- Your ESP32 firmware must implement the same protocol and translate incoming text/Braille commands into the actual LED or actuator output. This project does not claim to control a custom six-pin actuator until the matching firmware protocol is implemented and tested.
- Android speech recognition availability and behaviour depend on the speech recognition service installed on the phone.

## Important status
This is a new source project, not a compiled or device-tested release. Build it with GitHub Actions or Android Studio and share the first build log if any errors occur. A successful CI build still needs real-phone testing for Bluetooth permissions, speech recognition, text-to-speech, and the ESP32 protocol before a customer release.
