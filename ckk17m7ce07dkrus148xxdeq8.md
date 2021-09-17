## Download YouTube videos or only audios through this library

### Installation

``` bash
$ brew install youtube-dl
```

### Download videos

``` bash
$ youtube-dl <youtube-link>

```

### Download only audio

- you need to install `ffmpeg` before trying this operation

``` bash
$ brew install ffmpeg
$ youtube-dl -x --audio-format mp3 <youtube-link>
```

### Example

``` bash
$ youtube-dl -x --audio-format mp3 https://www.youtube.com/watch?v=SlPhMPnQ58k
[youtube] SlPhMPnQ58k: Downloading webpage
[download] Destination: Maroon 5 - Memories (Official Video)-SlPhMPnQ58k.webm
[download] 100% of 3.11MiB in 00:09
[ffmpeg] Destination: Maroon 5 - Memories (Official Video)-SlPhMPnQ58k.mp3
Deleting original file Maroon 5 - Memories (Official Video)-SlPhMPnQ58k.webm (pass -k to keep)
```

### Further reading

- http://ytdl-org.github.io/youtube-dl/

<span>Photo by <a href="https://unsplash.com/@vmxhu?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Szabo Viktor</a> on <a href="https://unsplash.com/s/photos/youtube?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>