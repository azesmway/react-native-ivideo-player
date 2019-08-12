
## react-native-ivideo-player
React-native-ivideo-player is a react-native-video based video playback component. React Native > 0.40.0 is required.
<br/> This is a fork of <a href="https://github.com/Lizhooh/react-native-ivideo">react-native-ivideo</a>.

<a href="https://www.npmjs.com/package/react-native-ivideo-player"><img src="https://img.shields.io/npm/v/react-native-ivideo-player.svg?style=flat-square"></a>
<a href="https://www.npmjs.com/package/react-native-ivideo-player"><img src="https://img.shields.io/npm/dm/react-native-ivideo-player.svg?style=flat-square"></a>


> Currently, the performance is not tested on IOS.

__Features：__
- Basic playback features, friendly interface, progress control, evolving animation, and simple style.
- Fine-grained optimization, UI threads can maintain 60 FPS during playback, and JS threads can maintain 60 ~ 55 FPS.
- Provides full-screen playback.
- Supports formats such as MP4, M4A, FMP4, WebM, MKV, MP3, Ogg, WAV, MPEG-TS, MPEG-PS, FLV and ADTS (AAC).
- Support DASH, HlS and SmoothStreaming adaptive streaming.


<br />

#### Basic playback function

![](./image/index.png)

#### Full screen playback

![](./image/full.gif)

#### Fade out animation

![](./image/demo.gif)

### Installation
React-native-ivideo uses react-native-video, react-native-orientation, and react-native-linear-gradient. 
You need to install these dependencies yourself.

Package：

```bash
yarn add react-native-ivideo-player
# or
npm install --save react-native-ivideo-player
```

Link：

```bash
react-native link react-native-video
react-native link react-native-orientation
react-native link react-native-linear-gradient
```

In `android/build.gradle` modify the code：

```js
allprojects {
    repositories {
        mavenLocal()
        jcenter()
        maven {
            url 'https://maven.google.com'
        }
        maven {
            // All of React Native (JS, Obj-C sources, Android binaries) is installed from npm
            url "$rootDir/../node_modules/react-native/android"
        }
    }
}
```

### Usage

```js
import IVideo from 'react-native-ivideo-player';

<IVideo
    source={{ uri: url }}
    title='title'
    showFullscreenIcon={true}
    width='100%'
    height={240}
    actions={[{
        text: 'select 1',
        onPress: () => { },
    }, {
        text: 'select 2',
        onPress: () => { },
    }]}
/>
```

### Example
Please check [Sample code](./example/index.js)。

### Attributes

| name               | type          | default | description         |
| :----------------- | :------------ | :------ | :------------------ |
| width              | number、string | 100%    | Width of the video，__Required__       |
| height             | number、string | 240     | Height of the video，__Required__       |
| source             | object        | null    | Video data source，__Required__      |
| toolbarDuration    | number        | 6000    | Toolbar display duration
（ms）。      |
| toolbarSliderColor | string        | #f90    | Toolbar slider color。           |
| title              | string        | ''      | Title。           |
| showFullscreenIcon | bool          | false   | Whether to display the full screen button。           |
| showBackIcon       | bool          | true    | Whether to display the back button.  |
| autoPlay           | bool          | false   | Whether to automatically start playback after the video initialization is completed. |
| actions            | array         |  [{ text, onPress }]      | Actions |
| gradientColor      | array         | ['rgba(1, 1, 1, 0.45)', 'rgba(1, 1, 1, 0.24)', 'rgba(1, 1, 1, 0.45)'] | Color gradient shield layer. |

<br />

__Proptypes react-native-video-player：__

| name                   | type   | default | description          |
| :--------------------- | :----- | :------ | :------------------- |
| progressUpdateInterval | number | 500     | onProgress Call time difference（ms）。  |
| playInBackground       | bool   | false   | Whether the video plays in the background           |
| muted                  | bool   | false   | Whether it is muted.                |
| rate                   | number | 1.0     | The rate at which the video plays.             |
| repeat                 | bool   | false   | Whether to repeat the loop playback.            |
| resizeMode             | string | 'cover' | How the video fills the container.        |
| useTextureView         | bool   | false   | use or not useTextureView。 |
| volume                 | number | 1.0     | The sound size of the video.             |
| seek                   | number | 0       | The location where the playback starts.             |

<br />

__Events：__

| name               | type     | default | description      |
| :----------------- | :------- | :------ | :--------------- |
| onProgress         | function | d => d  | Video playback progress event.        |
| onBuffer           | function | d => d  | Fires when the video is cached.        |
| onLoadStart        | function | e => e  | Fires when the video is loaded.      |
| onLoad             | function | d => d  | Fires when the video is loaded.      |
| onFullscreen       | function | e => e  | Fires when the video enters full screen.      |
| onCancelFullscreen | function | e => e  | Fires when the video exits full screen.      |
| onPlay             | function | e => e  | Fires when the video plays.        |
| onPause            | function | e => e  | Fires when the video is paused.      |
| onEnd              | function | e => e  | Fires when the video ends.      |
| onError            | function | e => e  | Fires when an error occurs in video playback/loading. |
| onBack             | function | e => e  | Fires when a click returns. |

### Methods

| name               | type     |  description                              |
| :----------------- | :------- |  :--------------------------------------- |
| play        | function |  Play the video.      |
| pause       | function |  Pause the video。        |
| seek        | function |  Change the progress position of the video.  |
| replay     | function |  Replay the video.      |

### Update logs
-  v2.0.0: Rewrite the code, fix some bugs, and add full-screen adaptive video orientation.
-  v1.6: Newly added partial sharing methods.
-  v1.5: Added the actions parameter.

