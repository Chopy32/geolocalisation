<template>
    <div id="map"></div>
</template>

<script>
    export default {
        name: "OpenStreetMap",
        props : {
            lon : 0,
            lat : 0
        },
        mounted : function () {

            var mymap = Y.map('map', {
                center: [this.lat,this.lon],
                zoom: 17,
                zoomControl: false,
                scrollWheelZoom: false
            });

            Y.tileLayer('https://api.tiles.mapbox.com/v4/{id}/{z}/{x}/{y}.png?access_token=pk.eyJ1IjoiYmVscG9ybyIsImEiOiJjam1hZ3ZkZjkwaTk5M3NwdHBrc25rdWRnIn0.CCcVioYTk3eDHHsD_y04Mw', { /* set your personal MapBox Access Token */
                maxZoom: 20, /* zoom limit of the map */
                attribution: '', /* set the map's caption */
                id: 'mapbox.satellite' /* mapbox.light / dark / streets / outdoors / satellite */
            }).addTo(mymap);

            Y.marker([this.lat, this.lon]).addTo(mymap); /* set your location's GPS Coordinates : [LAT,LON] */

        }
    }
</script>

<style scoped>
    #map {
        height: 100%;
        width: 100%;
    }
</style>