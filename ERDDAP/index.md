---
layout: leaflet
---
## ERDDAP

This site is currently under construction and is provided AS IS to serve as a reference for similiar endeavours by open data enthusiasts.

<form name="analyze" id="analyze" action="analyze.html" method="GET">
<table border="0" width="100%"><tbody>
<tr><td colspan="2">
        <select name="pagesize" id="pagesize"><option value="24">24</option><option value="48">48</option><option value="96">96</option></select>
        <div name="stations" id="stations"></div><br />
        <input id = "firstpage" name="firstpage" type="button" value="&lt;&lt;" /><input id = "formerpage" name="formerpage" type="button" disabled="1" value="Previous" />
        <input id = "nextpage" name="nextpage" type="button" value="Next" disabled="1" /><input id = "lastpage" name="lastpage" type="button" value="&gt;&gt;" /><br />
        <input type="hidden" id="csv" name="csv" disabled="1" readonly="1" style="display:'none';" value="" />
        <textarea  id="ticker" rows="4" cols="125" name="ticker" disabled="1" readonly="1" ></textarea> 
</td></tr><tr><td width="50%">
<div name="datasets" id="datasets"></div>
</td><td>
    <select name="field" id="field"><option value="T" selected="1">Temperature</option><option value="P">Pressure</option><option value="W">Wind</option></select>
    <div id="graphs"></div>
</td></tr>
</tbody></table>
</form>

<script>
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

<script type="text/python" src="/assets/py/erddap.bry"></script>

### Browse the source

This site and the pages it links to can be viewed as source files at [github](https://github.com/StephenMottyNRC/StephenMottyNRC.github.io). 
