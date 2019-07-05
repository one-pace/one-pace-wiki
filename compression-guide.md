# Raws
Ideally always go with the raws with the best quality. There are multiple factors to look into such as resolution and bitrate but in the end the best compression wins with the best quality. Also don't be afraid of file size. As long as they're under 1GB each it's fine. If the raw has to be re-encoded and it's 1080p you might as well downscale it to 720p right away.

# Project settings
Make sure the project properties in vegas match the raws frame rate and resolution. (Ctrl+Enter to check the properties) The field order should be Progressive scan. Disable resample mode. Turn off adjusting source media. No deinterlacing. No motion blur. 1.00000000 pixel aspect ratio.

# Rendering
Render with the lossless YUV preset. Make sure to match the resolution and frame rate of the raw. If the raws have differing frame rates use the higher one.

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
