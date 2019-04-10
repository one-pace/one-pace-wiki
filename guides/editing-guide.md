# Table of Contents
- [3. Configuration](#3-configuration)
  * [3.1. Project configuration](#31-project-configuration)
  * [3.2. Rendering configuration](#32-rendering-configuration)
  * [3.3. Compression configuration](#33-compression-configuration)
    + [3.3.1. Frame rate](#331-frame-rate)
    + [3.3.2. Video codec](#332-video-codec)
    + [3.3.3. Compressing](#333-compressing)
- [4. Raws](#4-raws)
  * [4.1. Acceptable raws](#41-acceptable-raws)
  * [4.2. Raws veg containers](#42-raws-veg-containers)
- [5. Editing](#5-editing)
  * [5.1. Timeline](#51-timeline)
  * [5.2. Editing music](#52-editing-music)
  * [5.3. Handling transitions](#53-handling-transitions)
  * [5.4. Following the mood](#54-following-the-mood)
  * [5.5. Still shots](#55-still-shots)

# 3. Configuration
## 3.1. Project configuration
These are the project settings that **all** Vegas project **must have** before starting editing.
![](https://i.imgur.com/VxWZ2Po.png)

## 3.2. Rendering configuration
The render template is based off the Sony AVC/MVC renderer template named `Internet 1280x720-30p`. Use the following configurations based on that.

![](https://i.imgur.com/aa5ElXM.png)
![](https://i.imgur.com/gixi4Au.png)
![](https://i.imgur.com/okPCPt0.png)

## 3.3. Compression configuration
For compression purposes we **always** use [ffmpeg](https://www.ffmpeg.org/download.html). This includes rendered episodes and streams.

### 3.3.1. Frame rate
The frame varies depending on the source material used. If the majority of the source material is using 23.976 as its frame rate, use the frame rate `24000/1001`. If, however, the majority of the source material uses the frame rate 29.976, use the frame rate `30000/1001`.

### 3.3.2. Video codec
For newly rendered episodes that are to be compressed to x265, use the video codec `libx265`. If you do not have that codec downloaded, check [here](https://trac.ffmpeg.org/wiki/Encode/H.265). For encoding streams, use the video codec `libx264`.


### 3.3.3. Compressing
Now that you've gathered all the important information on the frame rate and codecs to use, this is what to type in the terminal (Obviously, replace the tags with the correct information):

```ffmpeg -i <input.mp4> -c:v <video codec> -c:a copy -crf 23 -preset slow -r <frame rate> <output.mp4>```

# 4. Raws
## 4.1. Acceptable raws
For a raw to be accepted for use in One Pace it has to pass some criterias. If no raws can be found that match all the following criterias, the version that most closely matches the criterias (in descending priority order, combination of both audio and video from different raws possible) is the one we will use.

The following list decides the requirements for the video:

- No watermarks
- No signs such as ads, psa:s, and other texts that are not originally in the episode
- Nice stable framerate, smooth panning
- No artifacts or other video corruption that is not in the original episode
- No opening credits
- No opening lyrics

The following list decides the requirements for the audio:

- No ads or other audio that is not in the original episode
- No popping noises or other audio corruption that is not in the original episode

## 4.2. Raws veg containers
Raws veg containers, also called **Episode vegs**, help manage and control the source material used. Raws veg containers can crop unwanted black borders, globally adjust the volume of the source material, and host subtitle regions that can later be viewed and exported in the project. Doing these video changes manually in a project instead is unsustainable because it's not guaranteed that it's the only project that will use that source material.

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
