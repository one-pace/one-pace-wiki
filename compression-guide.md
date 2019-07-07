# Raws
Ideally always go with the raws with the best quality. There are multiple factors to look into such as resolution and bitrate but in the end the best compression wins with the best quality. Also don't be afraid of file size. As long as they're under 1GB each it's fine. If the raw has to be re-encoded and it's 1080p you might as well downscale it to 720p right away.

## Fix washed out colors
In the RAWS VEG, add LEVELS --> Studio RGB to Computer RGB preset. For some reason Vegas reads the colour space of the source file incorrectly, so this fixes the gamma shift that produces washed out blacks, and by extension different colours.

![](https://i.imgur.com/YaBW6Z9.png)

# Project settings
Make sure the project properties in vegas match the raws frame rate and resolution. (Ctrl+Enter to check the properties) The field order should be Progressive scan. Disable resample mode. Turn off adjusting source media. No deinterlacing. No motion blur. 1.00000000 pixel aspect ratio.

# Rendering
Make sure to match the resolution and frame rate of the raw. If the raws have differing frame rates use the higher one.

To render, ensure you have the Lagarith codec installed (https://lags.leetcode.net/codec.html). In Vegas, choose the HD 1080-24p YUV preset under the .AVI heading. Hit "Customize Template" and ensure that under "Video Format", it is changed to "Lagarith Lossless Codec". That may change your frame size and frame rate to different defaults, so be sure to swap those back to "Use Project Settings" and "23.976". Before comitting the render, just double check under "Configure..." next to Lagarith that it has the following settings.

![](https://i.imgur.com/37psvYm.png)

Once all is rendered, run the following command in FFMPEG: `ffmpeg -i "test.avi" -c:v libx265 -crf 18 -strict experimental -vf scale=1280x720:flags=lanczos -c:a aac -b:a 128k "encode1080.mp4"`

This introduces a new "-strict experimental" command since FFMPEG likes to whine and refuse to use lossless files with H265, but that's a warning to do with more complex render settings that have no relevance to us, so don't worry about it too much. 

This'll produce a render that should have identical colours and gamma to your original source files.

# Compression
Since avi has a weird audio codec you need to convert the audio codec to AAC. Make sure you match the audio bitrate of the raw. In the below example the audio bitrate is 128k.

This is the main command for compression, if your video is in 1080p, look below this command.
```
ffmpeg -i "input.avi" -c:v libx265 -c:a aac -b:a 128k -crf 18 "output.mp4"
```

Use this command if your video is in 1080p:
```
ffmpeg -i "input.avi" -c:v libx265 -c:a aac -b:a 128k -crf 18 -vf scale=1280x720:flags=lanczos "output.mp4"
```

## Streams
Encoding streams is annoying because of FFMpeg's path escape hell. Preferably make a .bat that you then run by dragging your .mkv file on there, so that you do some path escaping logic, example of batch code:
```
set sub_path=%~1
set sub_path=%sub_path:\=\\\\%
set sub_path=%sub_path::=\\:%
ffmpeg -i "%~1" -vf subtitles="%sub_path%" "%~n1.stream.mp4"
```
