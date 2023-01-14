# ffmpeg-tutorial
video processing in python using FFmpeg

Some basic FFmpeg commands:

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

sources:
 - https://shotstack.io/learn/use-ffmpeg-to-trim-video/
 - https://askubuntu.com/questions/396883/how-to-simply-convert-video-files-i-e-mkv-to-mp4
 - https://windowsloop.com/download-m3u8-video-with-ffmpeg/

Some other nice tutorials:
 - https://github.com/leandromoreira/ffmpeg-libav-tutorial
 
