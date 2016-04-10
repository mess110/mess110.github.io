---
layout: post
title: coinmarketcap json api
---

April 2014, the bitcoin hype is real. A nice website [https://coinmarketcap.com/](https://coinmarketcap.com/)
provides data about a lot of crypto currencies but it doesn't have a JSON API.

This is how [http://coinmarketcap.northpole.ro/](http://coinmarketcap.northpole.ro/) was born.

At the time of writing, the API served over **336 million** requests.

<div id="chartContainer" style="height: 200px; width: 100%; margin: 0px auto;"></div>

The API is growing because of its simplicity and the fact that I worked only
on [features requested by the users](https://www.reddit.com/r/coinmarketcapjson/).

As of April 2016, the API also provides [daily snapshots](http://coinmarketcap.northpole.ro/api/v5/history/) (a much requested feature).

Example API usage:

[http://coinmarketcap.northpole.ro/api/v5/BTC.json](http://coinmarketcap.northpole.ro/api/v5/BTC.json)
[http://coinmarketcap.northpole.ro/api/v5/history/BTC_2016.json](http://coinmarketcap.northpole.ro/api/v5/history/BTC_2016.json)

It is extremely satisfying [to see other people use the API](https://github.com/search?q=coinmarketcap.northpole.ro&type=Code&utf8=%E2%9C%93).

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
