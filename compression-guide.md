# Raws
Ideally always go with the raws with the best quality. There are multiple factors to look into such as resolution and bitrate but in the end the best compression wins with the best quality. Also don't be afraid of file size. As long as they're under 1GiB each it's fine.

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
