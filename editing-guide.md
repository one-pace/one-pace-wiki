# Table of Contents
- [1. Tools](#1-tools)
- [2. Source material containers](#2-source-material-containers)
- [3. Configuration](#3-configuration)
  * [3.1. Project configuration](#31-project-configuration)
  * [3.2. Rendering configuration](#32-rendering-configuration)
  * [3.3. Compression configuration](#33-compression-configuration)
    + [3.3.1. Frame rate](#331-frame-rate)
    + [3.3.2. Video codec](#332-video-codec)
    + [3.3.3. Compressing](#333-compressing)
- [4. Practices](#4-practices)
  * [4.1. Editing music](#41-editing-music)
  * [4.2. Handling transitions](#42-handling-transitions)
  * [4.3. Following the mood](#43-following-the-mood)
  * [4.4. Still shots](#44-still-shots)

# 1. Tools
# 2. Source material containers
Source material containers, also called **Episode vegs**, help manage and control the source material used. Source material containers can crop unwanted black borders, globally adjust the volume of the source material, and host subtitle regions that can later be viewed and exported in the project. Doing these video changes manually in a project instead is unsustainable because it's not guaranteed that it's the only project that will use that source material.

# 3. Configuration
## 3.1. Project configuration
These are the project settings that **all** Vegas project **must have** before starting editing.

- Resolution: 1280x720 for HD episodes (207+); 640x480 for SD episodes (1-206)
- Pixel aspect ratio: 1.0000
- Frame rate: 60.000
- Field order: None (Progressive scan)
- Deinterlace method: None
- Resample mode: Disable resample
- Adjust source media to better match project or render settings: NO
- Start all new projects with these settings: YES

## 3.2. Rendering configuration

## 3.3. Compression configuration
For compression purposes we **always** use [ffmpeg](https://www.ffmpeg.org/download.html). This includes rendered episodes and streams.

### 3.3.1. Frame rate
The frame varies depending on the source material used. If the majority of the source material is using 23.976 as its frame rate, use the frame rate `24000/1001`. If, however, the majority of the source material uses the frame rate 29.976, use the frame rate `30000/1001`.

### 3.3.2. Video codec
For newly rendered episodes that are to be compressed to x265, use the video codec `libx265`. If you do not have that codec downloaded, check [here](https://trac.ffmpeg.org/wiki/Encode/H.265). For encoding streams, use the video codec `libx264`.


### 3.3.3. Compressing
Now that you've gathered all the important information on the frame rate and codecs to use, this is what to type in the terminal (Obviously, replace the tags with the correct information):

```ffmpeg -i <input.mp4> -c:v <video codec> -c:a copy -crf 23 -preset slow -r <frame rate> <output.mp4>```

# 4. Practices
## 4.1. Editing music
## 4.2. Handling transitions
## 4.3. Following the mood
## 4.4. Still shots
Still shots are done by slowing down a video event to 0% speed and then extending it to the desired length. For the frame you wish to have a still shot of, separate it from the main video event, right-click it, and press "Insert/Remove Envelope" followed by "Velocity" and a green bar will display on the video event. At the beginning of the event right-click at the little green square and press "Set to 0% velocity", now you can drag your event as long as you want to and it will keep still, creating a still shot.
