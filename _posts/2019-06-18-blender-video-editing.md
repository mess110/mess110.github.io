---
layout: post
title: blender video editing
---

<center>
  <iframe width="560" height="315" src="https://www.youtube.com/embed/l4PZEEHZelg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</center>

Thats result. The footage was filmed with 2 GoPros on a chestmount filming at
1080p 60fps.

I copied all the video files in a folder. Thats the project folder. Went
through all the footage, noted down the timestamps of the scenes I wanted
in the video. I deleted all the videos I didn't need and made a backup
of the ones I needed.

In blender, I cut the videos accordingly and rendered them at 100%
resolution, MPEG-4, perceptually lossless, 60fps.

To speed up the render, I used [the video editors render script](https://github.com/mikeycal/the-video-editors-render-script-for-blender)
It splits blender render jobs to each CPU core you have.

Another cool blender addon I used is [power sequences](https://github.com/GDquest/Blender-power-sequencer),
mostly for fade effects, but it can do much more.

Color correction modifier for strips. Fiddle with the options a bit,
use the eye icon to inspect differences. Make sure you check different
frames of the video. Histogram helps, try to get a nice bell curve.

Add text and animate it with keyframes.

Added intro/outro images, searched for royalty free music and uploaded
the whole thing to youtube.

TODO for the future:

* credit music author in the video as well
* credits logo smaller so it can be covered by youtube subcribe button
* intro scene to get people hooked on watching, for example a few
seconds of high quality footage (sort of like clickbait)
* swoosh sound effect during transitions
* b-roll 4 seconds stable smooth motion in one direction
* text location not overlap youtube progress bar

## Cheatsheet

```
docker run -v $(pwd):/data jareware/ffmpeg -i input.mp4 -vf vidstabdetect out.mp4
docker run -v $(pwd):/data jareware/ffmpeg -i input.mp4 -vf vidstabtransform -y out.mp4
```
