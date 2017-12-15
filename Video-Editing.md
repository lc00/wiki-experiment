`ffmpeg -t 00:55:19 -i input.flv -vcodec copy -acodec copy output.flv`

* `-t HH:MM:SS` is the duration of the video, use this to trim
* `-ss HH:MM:SS` is the beginning of the video
* `-i` is the input file
* `-vcodec copy` and `-acodec copy` work on the stream directly, without any conversion
* The last argument is the output file
