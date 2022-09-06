# Project setup

1. Install [Flutter](https://docs.flutter.dev/get-started/install?gclid=CjwKCAjwvNaYBhA3EiwACgndgoXzQEzSyjqa0DalunZ02hzAtHW9vn_ZX5JHSUMotcKyfgd2z6M0yxoCx_AQAvD_BwE&gclsrc=aw.ds) and follow the setup instructions for your system and IDE.
2. Download [Android Studio](https://developer.android.com/studio?gclid=CjwKCAjwvNaYBhA3EiwACgndgirITZDaVNyEUvdiq8yxL06VDA0iFEfE65TYJfZ6VEEDGDVlnzwefBoC-JAQAvD_BwE&gclsrc=aw.ds).
3. Open Android Studio, and go to SDK Manager > SDK Tools > uncheck Hide Obselete Packages, and look for the NDK version 22, ensure it is checked. Apply and wait for the installation to complete.
4. Either run: `echo "ANDROID_NDK=(path to NDK)" >> ~/.gradle/gradle.properties`, or go to your user folder /.gradle/.gradle.properties and ensure it contains the line: ANDROID_NDK=(path to NDK), where the NDK path is the path to your version 22 NDK, which on Windows is: `ANDROID_NDK=C:\\Users\\[username]\\AppData\\Local\\Android\\Sdk\\ndk-bundle`. Make sure to you double slashes! (`\\`).
5. Install [Rust](https://www.rust-lang.org/tools/install).
6. Ensure that minimum JDK 8 is installed.
7. With a terminal opened **in the project folder**, run `rustup target add aarch64-linux-android armv7-linux-androideabi x86_64-linux-android i686-linux-android`
8. Open a terminal and run `cargo install cargo-ndk --version 2.6.0`
9. Generate the Rust code (explained below) and you're ready to go!

# Generating code

When modifications are made to rust code, make sure to build the code, so that it is compatible with the frontend. This is done through running `flutter_rust_bridge_codegen --rust-input rust/src/api.rs --dart-output lib/bridge_generated.dart`.

As Rust code is generated from api.rs, make sure to include `mod api` at the start of separate Rust files!
