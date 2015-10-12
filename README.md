# plasmapJS-tutorial
![a video demonstrating the use of plasmap.js](https://github.com/plasmap/plasmapJS-tutorial/demo.gif)

plasmapJS allows to retrieve geographical data and points of interest from plasmap.io. This is a tutorial illustrating how to get started using this technology.

In order to get going, **clone this repository** and have a look at the `.html` files.

There are currently three tutorials: Hello World, Composing Queries and Custom Callbacks.

## Hello World

This tutorial shows how to display the polygon representing the city
limits of the former German capital Bonn.
To see how, have a look at the file `tutorial1-hello-world.html`.
It sets up the basic frame for the subsequent tutorials.
This is this frame:

```html
<html>
  <head>
  <script src="plasmap.js"></script>
  <!-- These two following imports are necessary when using plasmapJS's default map, which we are.-->
  <link rel="stylesheet" href="http://cdn.leafletjs.com/leaflet-0.7.5/leaflet.css" />
  <script src="http://cdn.leafletjs.com/leaflet-0.7.5/leaflet.js"></script>
</head>
<body>
  <!-- This is all the HTML we need. A container which will hold our map that spans the entire viewport-->
  <div id="plasmap" style="height: 100%; width: 100%;"></div>

  <!-- All the necessary code is contained in this script tag-->
  <script type="text/javascript">
    /*************** CODE GOES HERE ****************/
  </script>
</body>
</html>
```
The code will always go inside the `<script>` tag.

The tutorial demonstrates how to get a hold of plasmap (`var P = Plasmap()`), create a channel over which to send queries (`var channel = P.channelWithDefaultMap()`), define a simple query (`city("Bonn")`) and finally how to submit this query for evaluation to the plasmap servers (`channel.send(query)`).


## Composing Queries

This tutorial shows how to combine two queries to form a new one.
We would like to display the districts of Bonn.
The districts query shows districts for a given city.
Have a look at the file `tutorial2-composing-queries.html`.
When writing `city("Bonn")`, plasmap only generates a query, but does
not run it. It is only ever run when sent over a channel.
More complex queries are achieved by means of composition, as in
`districts(city("Bonn"))`.

## Custom Callbacks

This tutorial shows how to intercept incoming server results and work
with them.
Plasmap's default callback displays the returned [(http://geojson.org)
GeoJSON] on plasmap's default map.
To do more fine grained operations one can supply a custom function
which is run whenever our client receives an object.
It has the following shape:
```javascript
function(geoJson) { ... }
```
The tutorial file is `tutorial3-custom-callbacks.html`.
