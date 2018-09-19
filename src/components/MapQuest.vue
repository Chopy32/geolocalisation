<template>
    <div id="map"></div>
</template>

<script>
    export default {
        name: "MapQuest",
        mounted : function () {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(function (position) {

                    var lon = position.coords.longitude
                    var lat = position.coords.latitude


                    L.mapquest.key = 'lYrP4vF3Uk5zgTiGGuEzQGwGIVDGuy24';

                    var map = L.mapquest.map('map', {
                        center: [lat, lon],
                        layers: L.mapquest.tileLayer('map'),
                        zoom: 12
                    });

                    map.addControl(L.mapquest.control());


                });
            } else {
                alert("Activez la géolocalisation sur votre navigateur")
            }
        }
    }
</script>

<style scoped>
    #map {
        height: 100%;
        width: 100%;
    }
</style>