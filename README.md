# mini-streaming-ffmpeg
Implementing a mini Video on demand streaming service with the help of ffmpeg, HLS(using `hls.js`).

### Commands
1. Open terminal and run this command, in the directory where the `input.mp4` file is stored
`ffmpeg -f mpegts -i input.mp4 -c:v libx264 -preset veryfast -f hls -hls_time 2 -hls_flags delete_segments stream.m3u8`

2. Create an `index.html` file like given below.
```index.html
// Index.html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Streaming with ffmpeg</title>
</head>

<body>
    <video id="video" controls autoplay width="600"></video>
    <script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
    <script>
        const video = document.getElementById("video");
        const hls = new Hls();
        hls.loadSource('stream.m3u8');
        hls.attachMedia(video);
    </script>

</body>
</html>
```

3. Open a python server
  `python3 -m http.server 5000`

4. Open a browser and go to `localhost:5000`
5. Boom, the video should be playing, once it loads.
