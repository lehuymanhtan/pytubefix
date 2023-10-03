# pytubefix

![PyPI - Downloads](https://img.shields.io/pypi/dm/pytubefix)
![PyPI - License](https://img.shields.io/pypi/l/pytubefix)
![PyPI - Version](https://img.shields.io/pypi/v/pytubefix)



### This python3 library is a solution to pytube's problem regarding update delays

## install:

    pip install pytubefix

----------
## usage:

```python

from pytubefix import YouTube
from pytubefix.cli import on_progress
 
url = input("URL >")
 
yt = YouTube(url, on_progress_callback = on_progress)
print(yt.title)
 
ys = yt.streams.get_highest_resolution()
ys.download()
```

----------

### If you want to save in .mp3 just pass the mp3=True parameter (note the real audio compression format is MP4A):


```python

from pytubefix import YouTube
from pytubefix.cli import on_progress
 
url = input("URL >")
 
yt = YouTube(url, on_progress_callback = on_progress)
print(yt.title)
 
ys = yt.streams.get_audio_only() # use this method -> get_audio_only()
ys.download(mp3=True) # pass the parameter mp3=Tre to save in .mp3
```

-----------

## if you want to download complete playlists:

```python

from pytubefix import YouTube
from pytubefix import Playlist
from pytubefix.cli import on_progress
 
url = input("URL Here >")

pl = Playlist(url)

for video in pl.videos:
    ys = video.streams.get_audio_only()
    ys.download(mp3=True) # pass the parameter mp3=True to save in .mp3

```
----------

## Subtitle/Caption Tracks:

#### viewing available subtitles:

```python

from pytubefix import YouTube

yt = YouTube('http://youtube.com/watch?v=2lAe1cqCOXo')
subtitles = yt.captions

print(subtitles)

```

#### printing the subtitle tracks:

```python

from pytubefix import YouTube
 

yt = YouTube('http://youtube.com/watch?v=2lAe1cqCOXo')

caption = yt.captions.get_by_language_code('en')
print(caption.generate_srt_captions())

```

#### now you can save subtitles to a txt file:

```python

from pytubefix import YouTube
 

yt = YouTube('http://youtube.com/watch?v=2lAe1cqCOXo')

caption = yt.captions.get_by_language_code('en')
caption.save_captions("captions.txt")

```

------------
## Using Channels:

#### get the channel name:

```python

from pytubefix import Channel

c = Channel("https://www.youtube.com/@ProgrammingKnowledge/featured")

print(f'Channel name: {c.channel_name}')

```

#### to download all videos from a channel:


```python

from pytubefix import Channel

c = Channel("https://www.youtube.com/@ProgrammingKnowledge")

print(f'Downloading videos by: {c.channel_name}')

for video in c.videos:
    download = video.streams.get_highest_resolution().download()

```
-----------

