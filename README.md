<!-- Copyright 2019 The FlutterCandies author. All rights reserved.
Use of this source code is governed by an Apache license
that can be found in the LICENSE file. -->

# Flutter WeChat Camera Picker

[![pub package](https://img.shields.io/pub/v/wechat_camera_picker?logo=dart&label=stable&style=flat-square)](https://pub.dev/packages/wechat_camera_picker)
[![pub package](https://img.shields.io/pub/v/wechat_camera_picker?color=42a012&include_prereleases&label=dev&logo=dart&style=flat-square)](https://pub.dev/packages/wechat_camera_picker)
[![GitHub stars](https://img.shields.io/github/stars/fluttercandies/flutter_wechat_camera_picker?logo=github&style=flat-square)](https://github.com/fluttercandies/flutter_wechat_camera_picker/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/fluttercandies/flutter_wechat_camera_picker?logo=github&style=flat-square)](https://github.com/fluttercandies/flutter_wechat_camera_picker/network)
[![Build status](https://img.shields.io/github/actions/workflow/status/fluttercandies/flutter_wechat_camera_picker/runnable.yml?branch=main&label=CI&logo=github&style=flat-square)](https://github.com/fluttercandies/flutter_wechat_camera_picker/actions/workflows/runnable.yml)
[![CodeFactor](https://img.shields.io/codefactor/grade/github/fluttercandies/flutter_wechat_camera_picker?logo=codefactor&logoColor=%23ffffff&style=flat-square)](https://www.codefactor.io/repository/github/fluttercandies/flutter_wechat_camera_picker)
[![GitHub license](https://img.shields.io/github/license/fluttercandies/flutter_wechat_camera_picker?style=flat-square)](https://github.com/fluttercandies/flutter_wechat_camera_picker/blob/master/LICENSE)
<a target="_blank" href="https://jq.qq.com/?_wv=1027&k=5bcc0gy"><img border="0" src="https://pub.idqqimg.com/wpa/images/group.png" alt="FlutterCandies" title="FlutterCandies"></a>

Language: English | [中文简体](README-ZH.md)

A **camera picker** based on WeChat's UI which is a separate runnable extension to
[wechat_assets_picker](https://pub.dev/packages/wechat_assets_picker).
The package based on `camera` for camera functions
and `photo_manager` for asset implementation.

Current WeChat version that UI based on: **8.3.x**
UI designs will be updated following the WeChat update in anytime.

See the [Migration Guide][] to learn how to migrate between breaking changes.

<details>
  <summary>Table of content</summary>

<!-- TOC -->
* [Flutter WeChat Camera Picker](#flutter-wechat-camera-picker)
  * [Features ✨](#features-)
  * [Screenshots 📸](#screenshots-)
  * [READ THIS FIRST ‼️](#read-this-first-)
  * [Preparing for use 🍭](#preparing-for-use-)
    * [Versions compatibility](#versions-compatibility)
    * [Setup](#setup)
      * [Android 13 (API 33) permissions](#android-13-api-33-permissions)
  * [Usage 📖](#usage-)
    * [Localizations](#localizations)
    * [Simple usage](#simple-usage)
    * [With configurations](#with-configurations)
    * [Using custom `State`s](#using-custom-states)
  * [Frequently asked question 💭](#frequently-asked-question-)
    * [Why the orientation behavior is strange on iOS?](#why-the-orientation-behavior-is-strange-on-ios)
  * [Contributors ✨](#contributors-)
<!-- TOC -->
</details>

## Features ✨

- ♿ Complete a11y support with _TalkBack_ and _VoiceOver_
- ♻️ Fully implementable with `State`s override
- 🎏 Fully customizable theme based on `ThemeData`
- 💚 Completely WeChat style (even more)
- ⚡️ Adjustable performance with different configurations
- 📷 Picture taking support
- 🎥 Video recording support
  - ⏱ Duration limitation support
  - 🔍 Scale when recording support
- ☀️ Exposure adjust support
- 🔍️ Scale with pinch support
- 💱 i18n support
  - ⏪ RTL language support
- 🖾 Foreground custom widget builder support
- 🕹️ Intercept saving with custom process

## Screenshots 📸

| ![](https://tva1.sinaimg.cn/large/007S8ZIlgy1ggtt6yrdqej30u01t017w.jpg) | ![](https://tva1.sinaimg.cn/large/007S8ZIlgy1ggtt6yh3x4j30u01t0wuo.jpg) |
|-------------------------------------------------------------------------|-------------------------------------------------------------------------|
| ![](https://tva1.sinaimg.cn/large/007S8ZIlgy1ggtt6z1h7xj30u01t01kx.jpg) | ![](https://tva1.sinaimg.cn/large/007S8ZIlgy1ggtt6zarvhj30u01t0x5f.jpg) |

## READ THIS FIRST ‼️

Be aware of below notices before you started anything:
- Due to understanding differences and the limitation of a single document,
  documents will not cover all the contents.
  If you find nothing related to your expected features and cannot understand about concepts,
  run the example project and check every options first.
  It has covered 90% of regular requests with the package.
- The package deeply integrates with the [photo_manager][photo_manager pub] plugin,
  make sure you understand these two concepts as much as possible:
  - Asset (photos/videos/audio) - [`AssetEntity`](https://pub.dev/documentation/photo_manager/latest/photo_manager/AssetEntity-class.html)
  - Assets collection (albums/libraries) - [`AssetPathEntity`](https://pub.dev/documentation/photo_manager/latest/photo_manager/AssetPathEntity-class.html)

When you have questions about related APIs and behaviors,
check [photo_manager's API docs][] for more details.

Most usages are detailed covered by the [example](example).
Please walk through the [example](example) carefully
before you have any questions.

## Preparing for use 🍭

### Versions compatibility

The package only guarantees to be working on **the stable version of Flutter**.
We won't update it in real-time to align with other channels of Flutter.

|        | 2.8.0 | 3.3.0 |
|--------|:-----:|:-----:|
| 4.0.0+ |   ❌   |   ✅   |
| 3.0.0+ |   ✅   |   ❌   |

If you got a `resolve conflict` error when running `flutter pub get`,
please use `dependency_overrides` to fix it.

### Setup

Run `flutter pub add wechat_camera_picker`,
or add `wechat_camera_picker` to `pubspec.yaml` dependencies manually.
```yaml
dependencies:
  wechat_camera_picker: ^latest_version
```

The latest **stable** version is:
[![pub package](https://img.shields.io/pub/v/wechat_camera_picker?logo=dart&label=stable&style=flat-square)](https://pub.dev/packages/wechat_camera_picker)

The latest **dev** version is:
[![pub package](https://img.shields.io/pub/v/wechat_camera_picker?color=9d00ff&include_prereleases&label=dev&logo=dart&style=flat-square)](https://pub.dev/packages/wechat_camera_picker)

Then import the package in your code:
```dart
import 'package:wechat_camera_picker/wechat_camera_picker.dart';
```

See also:
- [wechat_assets_picker#preparing-for-use](https://github.com/fluttercandies/flutter_wechat_assets_picker#preparing-for-use-)
- [camera#installation](https://pub.dev/packages/camera#installation)

#### Android 13 (API 33) permissions

When using the package, please upgrade
`targetSdkVersion` and `compileSdkVersion` to `33`.
Otherwise, no assets can be fetched on Android 13.

If you don't need to take photos or videos,
consider removing relevant permission in your apps, more specifically:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android">
    <!-- Add this if you need to take photos. -->
    <uses-permission android:name="android.permission.READ_MEDIA_IMAGES" />
    <!-- Add this if you need to take videos. -->
    <uses-permission android:name="android.permission.READ_MEDIA_VIDEO" />
</manifest>
```

## Usage 📖

### Localizations

When you're picking assets, the package will obtain the `Locale?`
from your `BuildContext`, and return the corresponding text delegate
of the current language.
Make sure you have a valid `Locale` in your widget tree that can be accessed
from the `BuildContext`. **Otherwise, the default Chinese delegate will be used.**

Embedded text delegates languages are:
* 简体中文 (default)
* English
* Tiếng Việt

If you want to use a custom/fixed text delegate, pass it through the
`CameraPickerConfig.textDelegate`.

### Simple usage

```dart
final AssetEntity? entity = await CameraPicker.pickFromCamera(context);
```

### With configurations

Use `CameraPickerConfig` for more picking behaviors.

```dart
final AssetEntity? entity = await CameraPicker.pickFromCamera(
  context,
  pickerConfig: const CameraPickerConfig(),
);
```

Fields in `CameraPickerConfig`:

| Name                          | Type                        | Description                                                                                           | Default Value                              |
|-------------------------------|-----------------------------|-------------------------------------------------------------------------------------------------------|--------------------------------------------|
| enableRecording               | `bool`                      | Whether the picker can record video.                                                                  | `false`                                    |
| onlyEnableRecording           | `bool`                      | Whether the picker can only record video. Only available when `enableRecording` is `true `.           | `false`                                    |
| enableTapRecording            | `bool`                      | Whether allow the record can start with single tap. Only available when `enableRecording` is `true `. | `false`                                    |
| enableAudio                   | `bool`                      | Whether Whether the picker should record audio. Only available with recording.                        | `true`                                     |
| enableSetExposure             | `bool`                      | Whether users can set the exposure point by tapping.                                                  | `true`                                     |
| enableExposureControlOnPoint  | `bool`                      | Whether users can adjust exposure according to the set point.                                         | `true`                                     |
| enablePinchToZoom             | `bool`                      | Whether users can zoom the camera by pinch.                                                           | `true`                                     |
| enablePullToZoomInRecord      | `bool`                      | Whether users can zoom by pulling up when recording video.                                            | `true`                                     |
| shouldDeletePreviewFile       | `bool`                      | Whether the preview file will be delete when pop.                                                     | `false`                                    |
| shouldAutoPreviewVideo        | `bool`                      | Whether the video should be played instantly in the preview.                                          | `false`                                    |
| maximumRecordingDuration      | `Duration?`                 | The maximum duration of the video recording process.                                                  | `const Duration(seconds: 15)`              |
| minimumRecordingDuration      | `Duration`                  | The minimum duration of the video recording process.                                                  | `const Duration(seconds: 1)`               |
| theme                         | `ThemeData?`                | Theme data for the picker.                                                                            | `CameraPicker.themeData(wechatThemeColor)` |
| textDelegate                  | `CameraPickerTextDelegate?` | Text delegate that controls text in widgets.                                                          | `CameraPickerTextDelegate`                 |
| resolutionPreset              | `ResolutionPreset`          | Present resolution for the camera.                                                                    | `ResolutionPreset.max`                     |
| cameraQuarterTurns            | `int`                       | The number of clockwise quarter turns the camera view should be rotated.                              | `0`                                        |
| imageFormatGroup              | `ImageFormatGroup`          | Describes the output of the raw image format.                                                         | `ImageFormatGroup.unknown`                 |
| preferredLensDirection        | `CameraLensDirection`       | Which lens direction is preferred when first using the camera.                                        | `CameraLensDirection.back`                 |
| lockCaptureOrientation        | `DeviceOrientation?`        | Whether the camera should be locked to the specific orientation during captures.                      | null                                       |
| foregroundBuilder             | `ForegroundBuilder?`        | The foreground widget builder which will cover the whole camera preview.                              | null                                       |
| previewTransformBuilder       | `PreviewTransformBuilder?`  | The widget builder which will transform the camera preview.                                           | null                                       |
| onEntitySaving                | `EntitySaveCallback?`       | The callback type define for saving entity in the viewer.                                             | null                                       |
| onError                       | `CameraErrorHandler?`       | The error handler when any error occurred during the picking process.                                 | null                                       |
| onXFileCaptured               | `XFileCapturedCallback?`    | The callback type definition when the XFile is captured by the camera.                                | null                                       |
| onMinimumRecordDurationNotMet | `VoidCallback?`             | The callback when the recording is not met the minimum recording duration.                            | null                                       |

### Using custom `State`s

All user interface can be customized through custom `State`s, including:
- `CameraPickerState`
- `CameraPickerViewerState`

After override `State`s, pass them through the picking method, more specifically:
- `CameraPicker.pickFromCamera(createPickerState: () => CustomCameraPickerState());`
- `CameraPickerViewer.pushToViewer(..., createViewerState: () => CustomCameraPickerViewerState());`

## Frequently asked question 💭

### Why the orientation behavior is strange on iOS?

Currently, the preview is not correctly synced on the iOS.
You can find more details in this issue:
https://github.com/flutter/flutter/issues/89216 .
Other than that, please submit issues to describe your question.

## Contributors ✨

Thank goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):
<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tbody>
    <tr>
      <td align="center" valign="top" width="14.28%"><a href="https://blog.alexv525.com"><img src="https://avatars1.githubusercontent.com/u/15884415?v=4?s=50" width="50px;" alt="Alex Li"/><br /><sub><b>Alex Li</b></sub></a><br /><a href="https://github.com/fluttercandies/flutter_wechat_camera_picker/commits?author=AlexV525" title="Code">💻</a> <a href="#design-AlexV525" title="Design">🎨</a> <a href="https://github.com/fluttercandies/flutter_wechat_camera_picker/commits?author=AlexV525" title="Documentation">📖</a> <a href="#example-AlexV525" title="Examples">💡</a> <a href="#ideas-AlexV525" title="Ideas, Planning, & Feedback">🤔</a> <a href="#maintenance-AlexV525" title="Maintenance">🚧</a> <a href="#question-AlexV525" title="Answering Questions">💬</a> <a href="https://github.com/fluttercandies/flutter_wechat_camera_picker/pulls?q=is%3Apr+reviewed-by%3AAlexV525" title="Reviewed Pull Requests">👀</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://www.kikt.top"><img src="https://avatars0.githubusercontent.com/u/14145407?v=4?s=50" width="50px;" alt="Caijinglong"/><br /><sub><b>Caijinglong</b></sub></a><br /><a href="#example-CaiJingLong" title="Examples">💡</a> <a href="#ideas-CaiJingLong" title="Ideas, Planning, & Feedback">🤔</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/LaelLuo"><img src="https://avatars3.githubusercontent.com/u/26056971?v=4?s=50" width="50px;" alt="Lael"/><br /><sub><b>Lael</b></sub></a><br /><a href="https://github.com/fluttercandies/flutter_wechat_camera_picker/commits?author=LaelLuo" title="Documentation">📖</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/mjl0602"><img src="https://avatars1.githubusercontent.com/u/32868496?v=4?s=50" width="50px;" alt="mjl0602"/><br /><sub><b>mjl0602</b></sub></a><br /><a href="https://github.com/fluttercandies/flutter_wechat_camera_picker/commits?author=mjl0602" title="Code">💻</a> <a href="#ideas-mjl0602" title="Ideas, Planning, & Feedback">🤔</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/siyukok"><img src="https://avatars0.githubusercontent.com/u/21030561?v=4?s=50" width="50px;" alt="AliasWang"/><br /><sub><b>AliasWang</b></sub></a><br /><a href="https://github.com/fluttercandies/flutter_wechat_camera_picker/commits?author=siyukok" title="Code">💻</a> <a href="#ideas-siyukok" title="Ideas, Planning, & Feedback">🤔</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/leftcoding"><img src="https://avatars.githubusercontent.com/u/7122926?v=4?s=50" width="50px;" alt="leftcoding"/><br /><sub><b>leftcoding</b></sub></a><br /><a href="https://github.com/fluttercandies/flutter_wechat_camera_picker/issues?q=author%3Aleftcoding" title="Bug reports">🐛</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/TheVinhLuong"><img src="https://avatars.githubusercontent.com/u/20371879?v=4?s=50" width="50px;" alt="Luong The Vinh"/><br /><sub><b>Luong The Vinh</b></sub></a><br /><a href="https://github.com/fluttercandies/flutter_wechat_camera_picker/commits?author=TheVinhLuong" title="Code">💻</a></td>
    </tr>
    <tr>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/luomo-pro"><img src="https://avatars.githubusercontent.com/u/41097395?v=4?s=50" width="50px;" alt="luomo-pro"/><br /><sub><b>luomo-pro</b></sub></a><br /><a href="#a11y-luomo-pro" title="Accessibility">️️️️♿️</a> <a href="https://github.com/fluttercandies/flutter_wechat_camera_picker/issues?q=author%3Aluomo-pro" title="Bug reports">🐛</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/ZhuBoao"><img src="https://avatars.githubusercontent.com/u/17305573?v=4?s=50" width="50px;" alt="LeonardoZhu"/><br /><sub><b>LeonardoZhu</b></sub></a><br /><a href="https://github.com/fluttercandies/flutter_wechat_camera_picker/commits?author=ZhuBoao" title="Code">💻</a></td>
      <td align="center" valign="top" width="14.28%"><a href="https://www.linkedin.com/in/loinp"><img src="https://avatars.githubusercontent.com/u/34020090?v=4?s=50" width="50px;" alt="Nguyen Phuc Loi"/><br /><sub><b>Nguyen Phuc Loi</b></sub></a><br /><a href="#translation-nploi" title="Translation">🌍</a></td>
    </tr>
  </tbody>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->
This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!

[photo_manager pub]: https://pub.dev/packages/photo_manager
[Migration Guide]: https://github.com/fluttercandies/flutter_wechat_camera_picker/blob/main/guides/migration_guide.md
