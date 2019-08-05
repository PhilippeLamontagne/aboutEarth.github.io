---
layout: leaflet
---
## SpotOn

This web page is reserved for use with the  [OpenStreetMap](https://www.openstreetmap.org/#map=3/71.34/-96.82) client "SpotOn".

<script>
    var map = L.map('map').setView([51.505, -0.09], 13);
    L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png?{foo}', {foo: 'bar'}).addTo(map);    
    L.marker([51.5, -0.09]).addTo(map)
      .bindPopup("<b>Hello world!</b><br />I am a popup.").openPopup();
    L.circle([51.508, -0.11], 500, {
      color: 'red',
      fillColor: '#f03',
      fillOpacity: 0.5
    }).addTo(map).bindPopup("I am a circle.");
    L.polygon([
      [51.509, -0.08],
      [51.503, -0.06],
      [51.51, -0.047]
    ]).addTo(map).bindPopup("I am a polygon.");
    var popup = L.popup();
    function onMapClick(e) {
      popup
        .setLatLng(e.latlng)
        .setContent("You clicked the map at " + e.latlng.toString())
        .openOn(map);
    }
    map.on('click', onMapClick);
</script>

### Browse the source

This site and the pages it links to can be viewed as source files at [github](https://github.com/StephenMottyNRC/StephenMottyNRC.github.io). 
