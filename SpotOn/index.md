---
layout: leaflet
---
## SpotOn

This web page is reserved for use with the  [OpenStreetMap](https://www.openstreetmap.org/#map=3/71.34/-96.82) client "SpotOn".

<form name="analyze" id="analyze" action="analyze.html" method="GET">
    <select name="pagesize" id="pagesize"><option value="12">12</option><option value="24">24</option><option value="48">48</option></select>
    <div name="stations" id="stations"></div><br />
    <input id = "firstpage" name="firstpage" type="button" value="&lt;&lt;" /><input id = "formerpage" name="formerpage" type="button" disabled="1" value="Previous" />
    <input id = "nextpage" name="nextpage" type="button" value="Next" disabled="1" /><input id = "lastpage" name="lastpage" type="button" value="&gt;&gt;" />
    <input type="hidden" id="csv" name="csv" disabled="1" readonly="1" style="display:'none';" value="" /></form>

<script>
#proj4.defs("urn:ogc:def:crs:EPSG::26915", "+proj=utm +zone=15 +ellps=GRS80 +datum=NAD83 +units=m +no_defs");
proj4.defs["OGC:CRS84"] = "+proj=longlat +ellps=WGS84 +datum=WGS84 +no_defs";
    
var map = L.map('map').setView([47.54, -54.47], 13);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: 'Data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

L.marker([47.54, -54.47]).addTo(map)
    .bindPopup('Start here')
    .openPopup();

async function updateGeoJSON(geoJSON) {
    L.Proj.geoJson(JSON.parse(geoJSON)).addTo(map);
}

</script>

<script type="text/python" src="/assets/py/spotOn.bry"></script>

### Browse the source

This site and the pages it links to can be viewed as source files at [github](https://github.com/StephenMottyNRC/StephenMottyNRC.github.io). 
