# android-build-signed-apk
A GitHub Action to clone repo, build APK and sign it with private build keystore

# Usage
`.github/workflows/build.yml`
```yml
name: Build

on:
  workflow_dispatch:
  push:

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4
      - uses: errr-maxx-build/android-build-signed-apk@master
        with:
          usePatchedSDK: true # optional
          buildType: release  # optional
          keyStore:         ${{ secrets.SIGNING_KEYSTORE }}
          keyStorePassword: ${{ secrets.SIGNING_KEYSTORE_PASSWORD }}
          keyAlias:         ${{ secrets.SIGNING_ALIAS }}
          keyPassword:      ${{ secrets.SIGNING_ALIAS_PASSWORD }}
          outputFile: ./app-release-signed.apk
```