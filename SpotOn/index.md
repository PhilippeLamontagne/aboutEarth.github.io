---
layout: leaflet
---
## SpotOn

This web page is reserved for use with the  [OpenStreetMap](https://www.openstreetmap.org/#map=3/71.34/-96.82) client "SpotOn".

<script>
var map = L.map('map').setView([47.54, -54.47], 13);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

L.marker([51.5, -0.09]).addTo(map)
    .bindPopup('A pretty CSS3 popup.<br> Easily customizable.')
    .openPopup();
</script>

### Browse the source

This site and the pages it links to can be viewed as source files at [github](https://github.com/StephenMottyNRC/StephenMottyNRC.github.io). 
