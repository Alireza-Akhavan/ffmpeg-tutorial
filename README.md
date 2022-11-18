# ffmpeg-tutorial
video processing in python using FFmpeg

Some basic FFmpeg commands:

## Convert Video by changing container

If you only want to convert MKV to MP4 then you will save quality and a lot of time by just changing the containers.
Both of these are just wrappers over the same content so the CPU only needs to do a little work.
Don't re encode as you will definitely lose quality.

`
ffmpeg -i LostInTranslation.mkv -codec copy LostInTranslation.mp4
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


sources:
 - https://shotstack.io/learn/use-ffmpeg-to-trim-video/
 - https://askubuntu.com/questions/396883/how-to-simply-convert-video-files-i-e-mkv-to-mp4
