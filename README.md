# vue-plyr
>A set of Vue components for the plyr video & audio player.

This is useful for when you want a nice video player in your Vue app.

## Installation

```bash
yarn add vue-plyr # or npm i vue-plyr --save
```

### Browser

Include the script file, then use it in the app; e.g.:

```html
<script type="text/javascript" src="https://unpkg.com/vue@latest"></script>
<script type="text/javascript" src="https://unpkg.com/vue-plyr@latest"></script>
<link rel="stylesheet" href="https://unpkg.com/vue-plyr@latest/dist/vue-plyr.css">
```

```js
Vue.use(VuePlyr)
```

### Module

```js
import VuePlyr from 'vue-plyr';
import 'vue-plyr/dist/vue-plyr.css';
Vue.use(VuePlyr)
```
#### Or
```js
import { PlyrVideo } from 'vue-plyr'
import 'vue-plyr/dist/vue-plyr.css'

export default {
    components: {
        PlyrVideo
    }
}
```

## Usage

Once installed, it can be used in a template as simply as:

```html
<!-- The preferred way to apply the component is by wrapping it with -->
<!-- the <plyr> tag. It has a lot more flexibility as you are able -->
<!-- to manage your element directly. -->
<plyr>
    <video>
        <source src="video.mp4" type="video/mp4" />
        <source src="video.ogg" type="video/ogg" />
    </video>
</plyr>
<plyr>
    <audio>
        <source src="audio.mp3" type="audio/mp3" />
        <source src="audio.ogg" type="audio/ogg" />
    </audio>
</plyr>
<plyr>
    <div data-type="youtube" data-video-id="bTqVqk7FSmY" />
</plyr>
<plyr>
    <div data-type="vimeo" data-video-id="147865858" />
</plyr>

<!-- You can also use the specific component and pass the necessary -->
<!-- data through the props. This way is not recommended, and will -->
<!-- probably be deprecated at some point. -->
<plyr-video poster="path/to/poster.png" :videos="this.videos" :subtitles="this.subtitles" :crossorigin="true" />
<plyr-audio :tracks="this.tracks" />
<plyr-youtube :id="this.youtubeID" />
<plyr-vimeo :id="this.vimeoID" />

```
```js
export default {
    data () {
        return {
            // Array of objects with path to video files and format.
            videos: [
                { src: 'path/to/video.mp4', format: 'mp4' },
                { src: 'path/to/video.webm', format: 'webm' }
            ],

            // Object with subtitles label, source, and language.
            subtitles: {
                label: "English Captions",
                src: "path/to/captions.vtt",
                srclang: "en"
            },

            // Array of objects with path to audio files and format.
            tracks: [
                { src: 'path/to/audio.mp3', format: 'mp3' },
                { src: 'path/to/audio.ogg', format: 'ogg' }
            ],

            // YouTube video ID or video URL.
            // https://www.youtube.com/watch?v=bTqVqk7FSmY & https://youtu.be/bTqVqk7FSmY would have the same effect.
            youtubeID: 'bTqVqk7FSmY',

            // Vimeo video ID or video URL.
            // https://vimeo.com/147865858 would have the same effect.
            vimeoID: '147865858'
        }
    }
}
```

In each of the elements you can pass an `options` prop which is an object that will be passed to the `plyr.setup()`
function. Info on that [here](https://github.com/sampotts/plyr#options).

## Author

**plyr-vue** © [RedXTech](https://github.com/redxtech), Released under the [MIT](./LICENSE.md) License.