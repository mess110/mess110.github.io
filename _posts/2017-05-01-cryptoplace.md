---
layout: post
title: cryptoplace
titleUrl: http://northpole.ro/cryptoplace/
---

<center>
  <a href="http://northpole.ro/cryptoplace/"><img src="/blog/images/cryptoplace/cryptoplace.png" /></a>
</center>
<center>
  <a href="https://www.reddit.com/r/place">/r/place</a> backed by the Bitcoin blockchain
</center>
<center>
  <a href="http://northpole.ro/cryptoplace">http://northpole.ro/cryptoplace/</a>
</center>

## Pixels on a canvas

On April 1st 2017, Reddit unleashed [/r/place](https://www.reddit.com/r/place/)
to the world. I like to think of it as a modern art experiment. A user could
change the color of a single pixel on a canvas every 5 minutes. This is what
came out of it:

<center>
  <a href="https://www.reddit.com/r/place/"><img src="/blog/images/cryptoplace/wc436nf7fdpy.png" /></a>
</center>

A similar experiment happened in 2005 when a student sold pixels on a canvas to fund
his university education. It was dubbed *The Million Dollar Homepage*. More on that
[here](https://en.wikipedia.org/wiki/The_Million_Dollar_Homepage).

## Would this work for Bitcoin?

The experiment starts with a 100x100 grid, each pixel having 16 BTC addresses
attached to it, one for each possible color. The address with the most bitcoin
received, decides the color of the pixel.

Let's look at the pixel at coordinates [45,52]. The green color of that pixel
has the address *1Fdi1pTd4rhUyDVtFPmCzTXpdVaxYKPzFi* and a balance of 0.01 BTC.
Out of all the colors which correspond to that pixel, green has the most BTC
received so the pixel is green. If you would like to make it red, you would need
to donate so the red address has more balance than the green balance.

I was really curious about using the blockchain as a database. I guess I found
a way :)

How does it work? On a server, I am running bitcoind in prune mode, I pre-generated
the addresses for each pixel and labeled them. A cronjob asks the bitcoind through
the RPC interface for the balance of each pixel and computes a JSON file and an image.
These 2 output files are than transferred to a server which serves [cryptoplace](http://northpole.ro/cryptoplace/).

For the frontend, I am using [Leaflet](https://github.com/Leaflet/Leaflet) and
[imgViewer2](https://github.com/waynegm/imgViewer2). After experimenting I think
I would have been happier if I implemented the UI from scratch - although the
libraries saved me a lot of time.

The code is open source, you can find it [here](https://github.com/mess110/cryptoplace/).

Would you like to see support for other crypto currencies? Which ones? I am happy to answer
any question you might have.

[Go ahead, you can draw anything!](http://northpole.ro/cryptoplace/)
