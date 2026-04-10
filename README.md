# mini-streaming-ffmpeg
Implementing a mini YouTube like streaming service with the help of ffmpeg, and protocols used are HLS.


`ffmpeg -f mpegts -i input.mp4 -i firstAudioTry.mp3 -c:v libx264 -preset veryfast -f hls -hls_time 2 -hls_flags delete_segments stream.m3u8`
