# Table of Contents
- [1. Tools](#1-tools)
- [2. Version control](#2-version-control)
- [3. Source material containers](#3-source-material-containers)
- [4. Configuration](#4-configuration)
  * [4.1. Project configuration](#41-project-configuration)
  * [4.2. Rendering configuration](#42-rendering-configuration)
  * [4.3. Compression configuration](#43-compression-configuration)
    + [4.3.1. Frame rate](#431-frame-rate)
    + [4.3.2. Video codec](#432-video-codec)
    + [4.3.3. Compressing](#433-compressing)
- [5. Editing](#5-editing)
  * [5.1. Editing music](#51-editing-music)
  * [5.2. Handling transitions](#52-handling-transitions)
  * [5.3. Following the mood](#53-following-the-mood)
  * [5.4. Still shots](#54-still-shots)

# 1. Tools
These are the tools that you will need as an editor:
- Vegas Pro 14.0
- FFmpeg
- Nextcloud
- git
- GitHub Desktop

# 2. Version control
For version control, we're using GitHub Desktop. Commit every time you finish a cut or performed any work that can be described in one sentence, e.g. "Removed filler scene", "Fixed popping noise", "Shortened lengthy sequence". The commit messages should be detailed enough that any editor can simply look in the history and know exactly what's changed. This is extra important since the .veg project files are binaries, meaning the file diffs aren't displayed. Do not include any changes in your commit that aren't related to the commit message.

Each episode is separated into its own branch, following the GitHub naming convention of lowercase words separated by dashes, e.g. "whole-cake-island-23", "marineford-09", "romance-dawn-02". Branches are only merged after release, and are then deleted.

# 3. Source material containers
Source material containers, also called **Episode vegs**, help manage and control the source material used. Source material containers can crop unwanted black borders, globally adjust the volume of the source material, and host subtitle regions that can later be viewed and exported in the project. Doing these video changes manually in a project instead is unsustainable because it's not guaranteed that it's the only project that will use that source material.

# 4. Configuration
## 4.1. Project configuration
These are the project settings that **all** Vegas project **must have** before starting editing.
![](https://i.imgur.com/VxWZ2Po.png)

## 4.2. Rendering configuration
The render template is based off the Sony AVC/MVC renderer template named `Internet 1280x720-30p`. Use the following configurations based on that.

![](https://i.imgur.com/aa5ElXM.png)
![](https://i.imgur.com/gixi4Au.png)
![](https://i.imgur.com/okPCPt0.png)

## 4.3. Compression configuration
For compression purposes we **always** use [ffmpeg](https://www.ffmpeg.org/download.html). This includes rendered episodes and streams.

### 4.3.1. Frame rate
The frame varies depending on the source material used. If the majority of the source material is using 23.976 as its frame rate, use the frame rate `24000/1001`. If, however, the majority of the source material uses the frame rate 29.976, use the frame rate `30000/1001`.

### 4.3.2. Video codec
For newly rendered episodes that are to be compressed to x265, use the video codec `libx265`. If you do not have that codec downloaded, check [here](https://trac.ffmpeg.org/wiki/Encode/H.265). For encoding streams, use the video codec `libx264`.


### 4.3.3. Compressing
Now that you've gathered all the important information on the frame rate and codecs to use, this is what to type in the terminal (Obviously, replace the tags with the correct information):

```ffmpeg -i <input.mp4> -c:v <video codec> -c:a copy -crf 23 -preset slow -r <frame rate> <output.mp4>```

# 5. Editing
## 5.1. Timeline
With the amount of cuts that we do in our episodes it's easy to get a messy timeline consisting of 10+ tracks making it hard to navigate and maintain your timeline. To avoid this make sure to follow these steps.

First off, video is above, audio is below. Anytime you want to add a video track, do it from the top, and vice versa for the audio. This way we get a simple and intuitive split between the two. Do not change the volume on any audio tracks under any circumstances. If you need to adjust the volume on a clip, do it separately through the volume slider on the relevant clip. Changing the volume on an entire audio track makes it completely useless for any clips other than the one clip you're changing the volume on, and is one big factor to why track bloating happens. You want to keep your tracks neat, close and tidy together so that you have pretty much everything in one place.

Never make a "stair" of audio or video events. This is where you don't use the unused space above/below a audio/video track but rather just keep adding tracks. You want to take every opportunity you get to use the closest unused space from the middle as possible. To avoid track bloating this is very important. :x: [Bad](https://i.imgur.com/sGFwMiz.png) :heavy_check_mark: [Good](https://i.imgur.com/RBPdESo.png)

Don't keep unedited cuts. This creates unnecessary complexity and easy confusion. If you undid a cut, make sure you put it together again. :x: [Bad](https://i.imgur.com/OYIKF48.png) :heavy_check_mark: [Good](https://i.imgur.com/krsBpFq.png)

## 5.2. Editing music
## 5.3. Handling transitions
## 5.4. Following the mood
## 5.5. Still shots
Still shots are done by slowing down a video event to 0% speed and then extending it to the desired length. For the frame you wish to have a still shot of, separate it from the main video event, right-click it, and press "Insert/Remove Envelope" followed by "Velocity" and a green bar will display on the video event. At the beginning of the event right-click at the little green square and press "Set to 0% velocity", now you can drag your event as long as you want to and it will keep still, creating a still shot.
