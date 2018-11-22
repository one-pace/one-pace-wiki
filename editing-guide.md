# Table of Contents
- [1. Configuration](#1-configuration)
  * [1.1. Project configuration](#11-project-configuration)
  * [1.2. Rendering configuration](#12-rendering-configuration)
  * [1.3. Compression configuration](#13-compression-configuration)
    + [1.3.1. Frame rate](#131-frame-rate)
    + [1.3.2. Video codec](#132-video-codec)
    + [1.3.3. Compressing](#133-compressing)
- [2. Practices](#2-practices)
  * [2.1. Editing music](#21-editing-music)
  * [2.2. Handling transitions](#22-handling-transitions)
  * [2.3. Following the mood](#23-following-the-mood)

# 1. Configuration
## 1.1. Project configuration
These are the project settings that **all** Vegas project **must have** before starting editing.

- Resolution: 1280x720 for HD episodes (207+); 640x480 for SD episodes (1-206)
- Pixel aspect ratio: 1.0000
- Frame rate: 60.000
- Field order: None (Progressive scan)
- Deinterlace method: None
- Resample mode: Disable resample
- Adjust source media to better match project or render settings: NO
- Start all new projects with these settings: YES

## 1.2. Rendering configuration

## 1.3. Compression configuration
For compression purposes we **always** use [ffmpeg](https://www.ffmpeg.org/download.html). For compressing a newly rendered episode, use this setting:

### 1.3.1. Frame rate
The frame varies depending on the source material used. If the majority of the source material is using 23.976 as its frame rate, use the frame rate `24000/1001`. If, however, the majority of the source material uses the frame rate 29.976, use the frame rate `30000/1001`.

### 1.3.2. Video codec
For newly rendered episodes that are to be compressed to x265, use the video codec `libx265`. If you do not have that codec downloaded, check [here](https://trac.ffmpeg.org/wiki/Encode/H.265). For encoding streams, use the video codec `libx264`.


### 1.3.3. Compressing
Now that you've gathered all the important information on the frame rate and codecs to use, this is what to type in your terminal (Obviously, replace the tags with your correct information):

```ffmpeg -i <input.mp4> -c:v <video codec> -c:a copy -crf 23 -preset slow -r <frame rate> <output.mp4>```

# 2. Practices
## 2.1. Editing music
## 2.2. Handling transitions
## 2.3. Following the mood
