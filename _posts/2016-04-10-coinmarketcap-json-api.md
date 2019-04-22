---
layout: post
title: coinmarketcap json api
---

April 2014, the bitcoin hype is real. A nice website [https://coinmarketcap.com/](https://coinmarketcap.com/)
provides data about a lot of crypto currencies but it doesn't have a JSON API.

This is how [https://coinmarketcap.northpole.ro/](https://coinmarketcap.northpole.ro/) was born.

At the time of writing, the API served over **336 million** requests.

<div id="chartContainer" style="height: 200px; width: 100%; margin: 0px auto;"></div>

The API is growing because of its simplicity and the fact that I worked only
on [features requested by the users](https://www.reddit.com/r/coinmarketcapjson/).

As of April 2016, the API also provides [daily snapshots](https://coinmarketcap.northpole.ro/history.json?coin=bitcoin&period=2016) (a much requested feature).

Example API usage:

[https://coinmarketcap.northpole.ro/ticker.json?identifier=bitcoin,dogecoin](https://coinmarketcap.northpole.ro/ticker.json?identifier=bitcoin,dogecoin)
[https://coinmarketcap.northpole.ro/history.json?coin=bitcoin&period=2016](https://coinmarketcap.northpole.ro/history.json?coin=bitcoin&period=2016)

It is extremely satisfying [to see other people use the API](https://github.com/search?q=coinmarketcap.northpole.ro&type=Code&utf8=%E2%9C%93).

The full documentation can be found [here](https://app.swaggerhub.com/apis/mess110/CoinMarketCap-Json-Api/v8).

HTTPS and CORS enabled.

# April 2019 update

I decided to stop hosting the service. Have some new fun projects which I would like to try working on and devote more of my resources to.

Thank you everyone who used the api. We passed 0.5 billion requests made. At one point I stopped counting because it took to long.
At one point, due to the usage, the hosting company contacted me to check if I was hacked or something because I had quite an amount of traffic. Turns out I wasn't
hacked, everything looked ok. I did tighten up the security at that point.
This is a follow up post, giving more details and sharing some of the things I learned.

Number 1 is a no brainer, I learned I need to learn more. Seeing my code over the span of 5 years on the same project really helped outline some of my flaws
and showed me what I need to work on.

The idea started off as a simple script which scraps `coinmarketcap.com` and saves the files to disk. The files can be served by a webserver. Bam, no db, simple
api, static pages for the website, self generating documentation, SEO optimised, subreddit, twitter and we are good to go. This is how it started.

What didn't I do? Start measuring from day 1. I wish I had done this sooner. Adding `munin` to measure the server performance helped me a lot in trying to
optimise the script and the server. Sometimes the load was overwhelming but looking at the right params showed me exactly what needs to happen.
For example, fewer reads from the file system would speed up the script. You know what that means? Caching.

Which lead to other problems.. I was using `mongodb` as a caching layer which sort of worked. My problem was that on the server I had limited space and between
all the logs, (which reminds me, setup log rotation!), the actual coin data, I also needed space for the db now.

I counted usage by parsing the logs. Until I ran out of space. At one point I stopped counting. But I still looked at apache logs.

Apache needed to be changed to nginx when I decided to use `ki` my tiny webframework. You probably see where this is going. We now had an API! But what about
the older APIs? Simple, just convert them. Make a new version. Deprecate older. We good.

Oh yea. Initially I said I wouldn't deprecate APIs. Because in my mind, I could just keep creating folders like v2, v3 when `coinmarketcap.com` changed. Little did
I know at that time that I would end up having a db, an API which actually does some stuff, caching. Also, I ran out of space. Use `ncdu` to find used space on
the file system. Great program.

I also started getting contributions with code which felt great. Thanks again. Doing a github search for `coinmarketcap.northpole.ro` we get quite a bit of results:

<center>
  <a href="https://github.com/search?q=coinmarketcap.northpole.ro&type=Code&utf8=%E2%9C%93"><img src="/blog/images/coinmarketcap/github_search.png" /></a>
</center>

124 code results at the time of writing. Isn't it super funny that the first result says "backward compatible" and the next visibile line contains `discontinued`?
Wish I would have comunicated more with my users. Sometimes I would reply to comments many months old, which I am sure was not that helpful. Setup notifications
to fix this.

I suspect this is why users would email me directly when there was a problem with the API. Thank you so much for your patience :D

I think that about covers some of the major things which happened with this API. Usage exploaded, felt humbling, see you around!

<script type="text/javascript" charset="utf-8">
  var GRAPH = [{ "x": 1396299600,"y": 3245515},{ "x": 1398891600,"y": 6185346},{ "x": 1401570000,"y": 12274216},{ "x": 1404162000,"y": 6160358},{ "x": 1406840400,"y": 2831308},{ "x": 1409518800,"y": 4267506},{ "x": 1412110800,"y": 3795583},{ "x": 1414792800,"y": 4623107},{ "x": 1417384800,"y": 3495375},{ "x": 1420063200,"y": 15310181},{ "x": 1422741600,"y": 14035313},{ "x": 1425160800,"y": 32372996},{ "x": 1427835600,"y": 27115318},{ "x": 1430427600,"y": 19192559},{ "x": 1433106000,"y": 15534402},{ "x": 1435698000,"y": 15757127},{ "x": 1438376400,"y": 26497918},{ "x": 1441054800,"y": 24020274},{ "x": 1443646800,"y": 19215801},{ "x": 1446328800,"y": 21260041},{ "x": 1448920800,"y": 11599628},{ "x": 1451599200,"y": 20000116},{ "x": 1454277600,"y": 14229074},{ "x": 1456783200,"y": 13634831}];
</script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/canvasjs/1.7.0/canvasjs.min.js" type="text/javascript" charset="utf-8"></script>
<script type="text/javascript">
  window.onload = function () {
    var dataPoints = []
    for (var i = 0; i < GRAPH.length; i++) {
      dataPoints.push({
        x: new Date(GRAPH[i]['x'] * 1000),
        y: GRAPH[i]['y']
      });
    }
    var chart = new CanvasJS.Chart("chartContainer",
    {
      theme: "theme2",
      title:{
        text: "api calls - per month"
      },
      axisX: {
      },
      axisY:{
        includeZero: false
      },
      data: [
      {
        type: "line",
        lineThickness: 3,
        dataPoints: dataPoints
      }
      ]
    });
    chart.render();
  }
</script>
