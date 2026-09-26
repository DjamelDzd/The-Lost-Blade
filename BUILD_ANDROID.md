# Android build notes

The project is configured for Android with package name `com.djamel.thelostblade`.

## Defold

Use a current stable Defold editor. The project was polished against the current 1.13-era project format; if you use a newer stable editor, open the project once and let Defold migrate resources if prompted.

## Local APK

Open the project in Defold and use:

`Project → Bundle → Android Application`

For a release APK, configure your Android signing/keystore in the Defold Android bundle settings.

## Bob / CI

Bob is Defold's command-line builder. Current Defold documentation notes that recent Bob versions require OpenJDK 25. Use the Bob version that matches the Defold release used for the project.

A release build must be signed with your own release keystore. Never commit the keystore or passwords into Git.

## GitHub Actions recommendation

- Store the keystore as an encrypted repository secret/file or use a protected CI secret.
- Store keystore password, key alias and key password as GitHub Actions secrets.
- Run Bob on a pinned Defold stable version.
- Upload the generated APK/AAB as an Actions artifact.
- Create a GitHub Release only after a physical-device test.
