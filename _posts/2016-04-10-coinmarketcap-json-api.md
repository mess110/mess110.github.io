---
layout: post
title: coinmarketcap json api
---

April 2014, the bitcoin hype is real. A nice website [https://coinmarketcap.com/](https://coinmarketcap.com/)
provides data about a lot of crypto currencies but it doesn't have a JSON API.

This is how [http://coinmarketcap.northpole.ro/](http://coinmarketcap.northpole.ro/) was born.

At the time of writing, the API served over **336 million** requests.

<!-- <div id="chartContainer" style="height: 200px; width: 100%; margin: 0px auto;"></div> -->

The API is growing because of its simplicity and the fact that I worked only
on [features requested by the users](https://www.reddit.com/r/coinmarketcapjson/).

It is extremely satisfying [to see other people use the API](https://github.com/search?q=coinmarketcap.northpole.ro&type=Code&utf8=%E2%9C%93).

<!-- <script src="http://coinmarketcap.northpole.ro/full_report.js" type="text/javascript" charset="utf-8"></script> -->
<!-- <script src="http://canvasjs.com/assets/script/canvasjs.min.js" type="text/javascript" charset="utf-8"></script> -->
<!-- <script type="text/javascript"> -->
  <!-- window.onload = function () { -->
    <!-- var dataPoints = [] -->
    <!-- for (var i = 0; i < GRAPH.length; i++) { -->
      <!-- dataPoints.push({ -->
        <!-- x: new Date(GRAPH[i]['x'] * 1000), -->
        <!-- y: GRAPH[i]['y'] -->
      <!-- }); -->
    <!-- } -->
    <!-- var chart = new CanvasJS.Chart("chartContainer", -->
    <!-- { -->
      <!-- theme: "theme2", -->
      <!-- title:{ -->
        <!-- text: "api calls - per month" -->
      <!-- }, -->
      <!-- axisX: { -->
      <!-- }, -->
      <!-- axisY:{ -->
        <!-- includeZero: false -->
      <!-- }, -->
      <!-- data: [ -->
      <!-- { -->
        <!-- type: "line", -->
        <!-- lineThickness: 3, -->
        <!-- dataPoints: dataPoints -->
      <!-- } -->
      <!-- ] -->
    <!-- }); -->
    <!-- chart.render(); -->
  <!-- } -->
<!-- </script> -->
