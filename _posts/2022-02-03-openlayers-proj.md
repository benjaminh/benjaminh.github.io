---
layout: post
title: Using custom projection with OpenLayers 6
date: 2022-02-03
description: A tutorial when struggling with OpenLayers and Lambert-93 projected data.
tags: openlayers SIG
categories: sample-posts
---
Using [OpenLayers](https://openlayers.org/) library can be challenging for many reasons, one of them being the number of ways it can be integrated into your application depending on your framework. And there are so many versions on the web it can be difficult to search for appropriate examples or help in debugging.

Besides, GIS is an exciting domain yet also challenging, especially when combined with web development. Managing data sources in different [spatial reference systems](https://en.wikipedia.org/wiki/Spatial_reference_system) to display them in a web page is an interesting subject to discuss. For example, OpenLayers 6 embeds `EPSG:3857` (WGS84/Pseudo-Mercator projected system) and `EPSG:4326` (WGS 84 geographic system) systems only so you have to get your hands a bit dirty if you work with a custom projection system. 

Here, I demonstrate the display of some GeoJSON data in Lambert-93 coordinate system (`EPSG:2154`, used for Metropolitan France), the definition of this CRS using Proj4, and the integration with OpenLayers 6 in a vanilla JS script.

The minimal HTML excerpt to load OpenLayers 6 and Proj4, while having a div to integrate map canvas:
{% highlight html linenos %}
<div id="map"></div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/proj4js/2.7.5/proj4.min.js"></script>
<script src="https://cdn.jsdelivr.net/gh/openlayers/openlayers.github.io@master/en/v6.12.0/build/ol.js"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/openlayers/openlayers.github.io@master/en/v6.12.0/css/ol.css">
{% endhighlight %}

And the vanilla JS script:
{% highlight js linenos %}

window.Proj4js = {
    Proj: function(code) {
        return proj4(Proj4js.defs[code]);
    },
    defs: proj4.defs,
    transform: proj4
};
      
proj4.defs("EPSG:2154","+proj=lcc +lat_1=49 +lat_2=44 +lat_0=46.5 +lon_0=3 +x_0=700000 +y_0=6600000 +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs");
ol.proj.proj4.register(proj4);

const lambert_proj = ol.proj.get('EPSG:2154');

var geojsonObject = {
"type": "FeatureCollection",
"name": "example_geojson",
"crs": { "type": "name", "properties": { "name": "urn:ogc:def:crs:EPSG::2154" } },
"features": [
{ "type": "Feature", "properties": { "name": "some_feature" }, "geometry": { "type": "MultiPolygon", "coordinates": [ [ [ [ 368318.11475041200174, 6591643.885249564424157 ], [ 368312.363392476399895, 6591649.636607498861849 ], [ 368319.94, 6591649.629999992437661 ], [ 368319.589999999618158, 6591648.559999990276992 ], [ 368318.11475041200174, 6591643.885249564424157 ] ] ] ] } },
]};

var features = new ol.format.GeoJSON().readFeatures(geojsonObject, {
  dataProjection: lambert_proj,
  featureProjection: 'EPSG:3857'
});

var vectorSource = new ol.source.Vector({ features: features });
var vectorLayer = new ol.layer.Vector({
  source: vectorSource,
  style: function (feature, resolution) {
    return new ol.style.Style({
    stroke: new ol.style.Stroke({
      color: 'black',
      width: 5,
    }),
    fill: new ol.style.Fill({
      color: 'rgba(255, 255, 0, 0.1)',
    }),
  });
  }
});

var map = new ol.Map({
  target: 'map',
  layers: [
    new ol.layer.Tile({ source: new ol.source.OSM() }),
    vectorLayer
  ],
  view: new ol.View({
    projection: "EPSG:3857",
    center: [0, 0],
    zoom: 2
  })
});

{% endhighlight %}

Some insights about this piece of code:
- lines 1-7 provide a wrapper for Proj4 declaration
- lines 9 and 10 are mandatory (omitting line 10 is a frequent mistake) to define **and** register the custom projection
- once defined and registered, one can access the new projection by calling the string code, here `EPSG:2154`, as demonstrated on line 12
- `geojsonObject` is a GeoJSON formatted string with a single feature, provided as a matter of example
- lines 22 to 25 are important: `geojsonObject` features are read by specifying `dataProjection` (i.e. input data projection system, here : `EPSG:2154`), and **reprojecting on the fly** to a destination CRS specified using `featureProjection` (here `EPSG:3857`)
- features are then loaded as a vector layer using basic OpenLayers methods (lines 27 to 41)
- finally, the map and view are instantiated while specifying the view projection, here `EPSG:3857`. The CRS defined here **must** be the same as the one declared in `featureProjection` above.

_Note_: one can test the same minimal example without using reprojection on the fly. Then, the view projection must be set as `lambert_proj` (aka `EPSG:2154`), and `featureProjection` can be omitted.