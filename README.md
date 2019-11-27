<html>
<head>
  <title>A Leaflet map!</title>
  <link rel="stylesheet" href="./Leaflet-1.0.3/leaflet.css"/>
  <script src="./Leaflet-1.0.3/leaflet.js"></script>
  <style>
    #map{ height: 100% }
  </style>
</head>
<body>

  <div id="map"></div>

  <script>
  // initialize the map
  var map = L.map('map').setView([42.35, -71.08], 13);
  // load a tile layer
  L.tileLayer('http://tiles.mapc.org/basemap/{z}/{x}/{y}.png',
    {
      attribution: 'Tiles by <a href="http://mapc.org">MAPC</a>, Data by <a href="http://mass.gov/mgis">MassGIS</a>',
      maxZoom: 17,
      minZoom: 9
    }).addTo(map);
    
    // base map
L.tileLayer('http://tiles.mapc.org/basemap/{z}/{x}/{y}.png',
{
  attribution: 'Tiles by <a href="http://mapc.org">MAPC</a>,
    Data by <a href="http://mass.gov/mgis">MassGIS</a>',
  maxZoom: 17,
  minZoom: 9
}).addTo(map);
// bike lanes
L.tileLayer('http://tiles.mapc.org/trailmap-onroad/{z}/{x}/{y}.png',
{
  maxZoom: 17,
  minZoom: 9
}).addTo(map); 
    
      // load GeoJSON from an external file
  $.getJSON("rodents.geojson",function(data){
    // add GeoJSON layer to the map once the file is loaded
    L.geoJson(data).addTo(map);
  });
 $.getJSON("rodents.geojson",function(data){
    var ratIcon = L.icon({
    iconUrl: 'rat.gif',
    iconSize: [50,40]
  }); 
  L.geoJson(data  ,{
    pointToLayer: function(feature,latlng){
	  return L.marker(latlng,{icon: ratIcon});
    }
  }  ).addTo(map);
});
  
  </script>
</body>
</html>
