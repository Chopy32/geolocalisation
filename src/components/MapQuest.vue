<template>
    <div id="map"></div>
</template>


<script>
    export default {
        name: "MapQuest",
        props : {
            lon : 0,
            lat : 0
        },
        mounted : function () {


            L.mapquest.key = 'lYrP4vF3Uk5zgTiGGuEzQGwGIVDGuy24';

            var map = L.mapquest.map('map',
                {
                center: [this.lat, this.lon],
                layers: L.mapquest.tileLayer('map'),
                zoom: 12
                }
            );

            map.addControl(L.mapquest.control());
        }
    }
</script>

<style scoped>
    #map {
        height: 100%;
        width: 100%;
    }
</style>