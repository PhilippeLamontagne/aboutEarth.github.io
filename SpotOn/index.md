---
layout: leaflet
---
## SpotOn

This web page is reserved for use with the  [OpenStreetMap](https://www.openstreetmap.org/#map=3/71.34/-96.82) client "SpotOn".

This site is currently under construction and is provided AS IS to serve as a reference for similiar endeavours by open data enthusiasts.

<table border="0"><tbody>
<tr><td style="width:640px">
    <form name="analyze" id="analyze" action="analyze.html" method="GET">
        <select name="pagesize" id="pagesize"><option value="12">12</option><option value="24">24</option><option value="48">48</option></select>
        <div name="stations" id="stations"></div><br />
        <input id = "firstpage" name="firstpage" type="button" value="&lt;&lt;" /><input id = "formerpage" name="formerpage" type="button" disabled="1" value="Previous" />
        <input id = "nextpage" name="nextpage" type="button" value="Next" disabled="1" /><input id = "lastpage" name="lastpage" type="button" value="&gt;&gt;" />
    <p />
    <table border="0"><tbody>
    <tr><td>Timestamp: </td><td colspan="2"><input  id="X" name="X" disabled="1" readonly="1" value="" /> </td></tr>
    <tr><td>Temperature: </td><td colspan="2"><input style="max-width:6em" id="T" name="T" disabled="1" readonly="1" value="" /> &deg;C</td></tr>
    <tr><td >Pressure: </td><td colspan="2"><input style="max-width:6em" id="P" name="P" disabled="1" readonly="1" value="" /> kPa</td></tr>
    <tr><td>Wind speed: </td><td><input style="max-width:6em" id="Ws" name="Ws" disabled="1" readonly="1" value="" /> kts
    </td><td>bearing: <input style="max-width:6em" id="Wb" name="Wb" disabled="1" readonly="1" value="" /> &deg;</td></tr>
    <tr><td colspan="3">Data Source: Environment and Climate Change Canada</td></tr>
    </tbody></table>
    <input type="hidden" id="csv" name="csv" disabled="1" readonly="1" style="display:'none';" value="" />
</form>
</td><td>
    <form name="visualize" id="visualize" action="visualize.html" method="GET">
    <select name="field" id="field"><option value="T" selected="1">Temperature</option><option value="P">Pressure</option><option value="W">Wind</option></select>
    <div id="graphs"></div>
</form>
</td></tr>
</tbody></table>

<script>
// proj4.defs("urn:ogc:def:crs:EPSG::26915", "+proj=utm +zone=15 +ellps=GRS80 +datum=NAD83 +units=m +no_defs");
proj4.defs("urn:ogc:def:crs:OGC:1.3:CRS84", "+proj=longlat +ellps=WGS84 +datum=WGS84 +no_defs");
    
var map = L.map('map').setView([47.54, -54.47], 13);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: 'Data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

//L.marker([47.54, -54.47]).addTo(map).bindPopup('Start here').openPopup();

var popup = L.popup();
function onMapClick(e) {
  popup
    .setLatLng(e.latlng)
    .setContent("You clicked the map at " + e.latlng.toString())
    .openOn(map);
}
map.on('click', onMapClick);

var layer = L.geoJSON();
layer.addTo(map);
async function updateGeoJSON(geoJSON) {
    layer.remove();
    layer = L.Proj.geoJson(JSON.parse(geoJSON));
    layer.addTo(map);
}

</script>

<script type="text/python" src="/assets/py/spotOn.bry"></script>

### Browse the source

This site and the pages it links to can be viewed as source files at [github](https://github.com/StephenMottyNRC/StephenMottyNRC.github.io). 
