# Android build notes

The project is configured for Android with package name `com.djamel.thelostblade`.

## Defold

Use Defold 1.13.1 or a newer stable editor. The project uses the 1.13.1-era project format; if a newer stable editor prompts for a resource migration, review and accept it only when you intend to update the project format.

## Local APK

Open the project in Defold and use:

`Project → Bundle → Android Application`

For a release APK, configure your Android signing/keystore in the Defold Android bundle settings.

## Bob / CI

Bob is Defold's command-line builder. The GitHub Actions workflow pins Bob 1.13.1 and OpenJDK 25. The equivalent release APK command is:

```sh
java -jar bob.jar \
  --platform arm64-android \
  --variant release \
  --archive \
  --bundle-format apk \
  --bundle-output build/android \
  --keystore android-release.keystore \
  --keystore-pass "$ANDROID_KEYSTORE_PASSWORD" \
  --keystore-alias "$ANDROID_KEY_ALIAS" \
  --key-pass "$ANDROID_KEY_PASSWORD" \
  resolve build bundle
```

Omit the keystore flags and use `--variant debug` for an installable debug APK. Bob creates a temporary debug signature when no release keystore is supplied.

A release build must be signed with your own release keystore. Never commit the keystore or passwords into Git.

## GitHub Actions recommendation

- Store the keystore as an encrypted repository secret/file or use a protected CI secret.
- Store keystore password, key alias and key password as GitHub Actions secrets.
- Run Bob on a pinned Defold stable version.
- Upload the generated APK/AAB as an Actions artifact.
- Create a GitHub Release only after a physical-device test.
