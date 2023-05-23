# ffmpeg-tutorial
video processing in python using FFmpeg

Some basic FFmpeg commands:

## Change Video Codec (Transcoding)

`
ffmpeg -i input.mp4 -c:v libx265 output.mp4
`

## Convert Video by changing container

If you only want to convert MP4 to AVI then you will save quality and a lot of time by just changing the containers.
Both of these are just wrappers over the same content so the CPU only needs to do a little work.
Don't re encode as you will definitely lose quality.

you can convert from mp4 to the container avi just by typing the follow command:

`
ffmpeg -i input.mp4 -codec copy output.avi
`

Or simply:

`
ffmpeg -i input.mp4 output.avi
`

It is called `remuxing` , which means converting from one container to another one.  There is another convertion which is called `transcoding`.

## compression

`
ffmpeg -i input.mp4 -vcodec libx265 -crf 28 output.mp4
`

`libx265` is a video codec that uses the H.265 compression standard to encode video data. 
It is a more efficient and advanced codec than its predecessor, H.264, which means it can achieve higher compression ratios while maintaining the same level of visual quality.

The `-crf` option in the ffmpeg command stands for "Constant Rate Factor". It is used to adjust the quality of the compressed video output. The CRF value ranges from `0 to 51`, with lower values indicating higher quality (and larger file sizes) and higher values indicating lower quality (and smaller file sizes).

In the given command, the CRF value is set to 28, which is a moderate value for maintaining a balance between quality and size. If you want to further compress the video by reducing its quality, you can increase the CRF value. 
For example, if you increase the CRF value by 4 or 6 units, say to 32 or 34, respectively, you will get a smaller file size but at the cost of reduced video quality. 
It's important to find the right balance between quality and size for your particular use case.


## Cut using a duration

`
ffmpeg -i input.mp4 -ss 00:05:20 -t 00:10:00 -c:v copy -c:a copy output1.mp4
`

-ss specifies the starting position.
-t specifies the duration from the start position.

## Cut using a specific time

`
ffmpeg -i input.mp4 -ss 00:05:10 -to 00:15:30 -c:v copy -c:a copy output2.mp4
`

The above command uses -to to specify an exact time.

## Stream download

Some stream websites:
https://kamery.ovanet.cz/
https://lahzenegar.com/Irancell/DataScience

Download M3U8 Video with FFmpeg

`
ffmpeg -i "http://example.com/video_url.m3u8" -c copy -bsf:a aac_adtstoasc "output.mp4"
`

[FFMpeg Copy Live Stream (Limit to 60s file)](https://stackoverflow.com/questions/58909322/ffmpeg-copy-live-stream-limit-to-60s-file)

`
ffmpeg -i source_hls.m3u8 -c copy -f segment -segment_time 60 -segment_wrap 2 -reset_timestamps 1 out%02d.mkv -y
`

Sources:
 - https://shotstack.io/learn/use-ffmpeg-to-trim-video/
 - https://askubuntu.com/questions/396883/how-to-simply-convert-video-files-i-e-mkv-to-mp4
 - https://windowsloop.com/download-m3u8-video-with-ffmpeg/

Official documentation:
 - https://www.ffmpeg.org/ffmpeg.html

Some other nice tutorials:
 - https://github.com/leandromoreira/ffmpeg-libav-tutorial
 
